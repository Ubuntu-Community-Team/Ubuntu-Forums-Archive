---
title: "Reordering data in ASCII file"
date: 2012-03-29
forum: General Help
---

### Post by JCM_Pico on 2012-03-29
Hi there,

I have a dataset in an ASCII file with no constant delimiter between the  data values, therefore all the ways that I know to import the data to  Matlab do not work...
The dataset is composed of strings and numbers, (I'm only interested in  the number) and I would like to verify the file line by line and if the  character "#" appears I want to save from column 13-16 in the first line  and column. Otherwise I would like to save from column 16-20 in the  following lines.... When the character "#" appears again I would like to  change column save the values in the first line and continue to save  the data in the following lines... and to keep doing it until the end of  the ASCII file..... And finally in the end save it to a nicely formatted ASCII with every column with constant separation....

Any suggestion of how to do this? in bash, fortran, python or matlab ;)

Thanks

---

