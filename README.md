# Bash completion script for MCNP

This is a bash completion script for MCNP. It complets the KEYWORD=value and other_options.
For most of the files the completion just searches for any file in the directory. Special
handling is available for inp=, runtpe=, mctal=, xsdir= and name=

If for the keywords inp, runtpe, mctal and xsdir the curser is positioned directly after the 
equal sign, these keywords only match the "normal" file names.
E.g. for runtpe the folowing files would be matched: runtpe, runtpf, <filename>.r <filename>.r.h5
For inp, only <filename>.i and <filename>.inp matches. 
If there is a space between the equal sign and the cursor, then again ANY filename is matched.
This allows to find non-standard filenames.

A special treatment is available for the name= keyword. If the inp keyword is already given on the 
input line, the name could be completed with the filename portion of the inp keyword. 
If the line is "mcnp inp=godiva.i name=" the name would be completed to "name=godiva." With that, mcnp 
generates the output files godiva.o and godiva.r.h5. This behaviour matches my personal preferences.

Last special treatment is for the TASKS command. The script checks it a MCNP_TASKS variable exists and 
inserts that after the TASKS. If the variable is not found, it tries to execute the nproc executable 
and falls back to 1 if that does not work.
