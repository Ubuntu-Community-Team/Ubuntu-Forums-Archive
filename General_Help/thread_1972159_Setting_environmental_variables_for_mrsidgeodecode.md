---
title: "Setting environmental variables for mrsidgeodecode"
date: 2012-05-03
forum: General Help
---

### Post by notbitmonk on 2012-05-03
I have some sid raster files that I would like to convert to geoTIFF. I downloaded the LizardTech command line tool ([http://www.lizardtech.com/downloads/tools.php](http://www.lizardtech.com/downloads/tools.php)) to perform this function. I opened up a terminal cd to the folder and tried to use the executable with no luck. In the accompanying README it said to set up the environmental variable. After a quick search of what this meant, I used the following code to set a session variable:
```
PATH=/home/jesse/Downloads/GeoExpressCLU/bin
```
Tried again and the error returned was the following:
> mrsidgeodecode: error while loading shared libraries: libgeos_c.so.1: cannot open shared object file: No such file or directory
The aforementioned library is in one of the folders supplied with the utility. I also tried copying the folder to /opt and setting the variable to the new path again with no luck. 
What are your suggestions?

---

### Post by jw06 on 2012-06-03
I just ran into the same problem, and found a solution that worked for me. After opening a terminal and changing to the directory containing the mrsidgeodecode binary, I was able to set the correct environmental variable by running:

```
export LD_LIBRARY_PATH=`pwd`
```After that, mrsidgeodecode ran with no errors.

---

### Post by notbitmonk on 2013-03-10
Unfortunately your solution did not work for me and I have not a "proper" solution. I checked the information on how to set environmental variables located at [https://help.ubuntu.com/community/EnvironmentVariables#Other_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#Other_environment_variables). I copied the extracted GeoExpress files to /opt. In my case I used the 32-bit folder. Afterwards I created geoexpress.conf in /etc/ld.so.conf.d. The contents were:
```

# LizardTech GeoExpress command line utilities
/opt/geoexpress
/opt/geoexpress/bin
/opt/geoexpress/libproject

```
To use mrsidgeodecode first I cd to /opt/geoexpress/bin. The I run ```
./mrsidgeodecode -i "INPUT FILE" -o "OUTPUT FILE.tifg" -wf
``` So far is working ok. A little hint. GeoTIFF can be specified as the output format by including the extension "tifg" as part of the output file name. Otherwise you will need to set the "of" option to "tifg". 
It is not a "proper" solution because I have to cd to the executable location. It is a "solution" because I can do what I need to.

---

