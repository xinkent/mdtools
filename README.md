# mcts_md
Python implementation for PACS_MD and MCTS_MD.
It uses GROMACS command for all of the manipulation　about MD simulation.
The required version is GROMACS 2018.1.
## USAGE
### equivration
Before running PaCS or PaTS MD, We have to do adding ion, energy minimization, nvt equilibration and npt equilibration.
We need the .mdp files to do each manipulation of such preparations. The .mdp files here are intended only for use with this chignolin(1uao) folding sample. You have to set the parameters for each of your tasks.  
```
initialize.py() 
```
### Requrements
Both PaCS and PaTS MD program require the files shown below.
- reactant structure (.gro)
- checkpoint file after the equilibration (.cpt)
- topology file (.top)
- target structure (.gro)
- mdp file for short md (.mdp)


### PACS MD
In the PaCS MD, the number of cycles is 100 and the number of parallele cascades is 5 in default configuration.
This program makes output files including trajectory file (merged_pacs.trr) and rmsd to the target structure (rmsd_pacs.xvg).
```
python pacs_md.py
```
### PaTS MD
```
python pats_md.py 
```
- Options
  - -r <.gro> : reactant structure file.
  - -t <.gro> : target structure file.
  - -top <.top> : topology file.
  - s : step size. default is 1000.
  - c : a parameter of ucb socre. default is 0.05.
  - cn : resume from the previous state. default is 0.
  - ntmpi : the number of mpi.
  - ntomp : the number of open MP
