---
title: "How to install mkl 8.0.2 library on Dapper beta release?"
date: 2006-05-03
forum: General Help
---

### Post by baleine on 2006-05-03
Hello,

Is there anyone who succeed installing mkl (intel library for ifort compiler) on UBUNTU? I have Dapper beta release and I have troubles!

I succeed installing ifort compiler 9.0, but by following the steps described on the HOW TO [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571)
rather than the only INTEL install.sh script (because it did not work). 
- Thanks to Gappy , the author -

BUT now, I am not able to install the mkl 8.0.2 library because the "install.sh" script seems not to be sufficient either.

Do I have to use the same steps described on the HOW TO [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571) ?
So do I have to modify the csh script make9?

I would be very glad if somebody could tell me how to do...](*,) 

baleine

---

### Post by jeremytaylor on 2006-06-14
Hi there, 
just in case you haven't figured this out yet the simplest thing to do is run the install script. At some point it will ask where to extract files to, you can leave this as the default /tmp/mkl.
Then when the installer fails go to /tmp/mkl and use alien to convert the rpm to a .deb
```
sudo alien --to-deb WHATEVER.rpm
```
then install using dpkg
```
sudo dpkg -i WHATEVER.deb
```

Jeremy

---

### Post by koara on 2007-02-16
> **jeremytaylor said:**
> Hi there, 
just in case you haven't figured this out yet the simplest thing to do is run the install script. At some point it will ask where to extract files to, you can leave this as the default /tmp/mkl.
Then when the installer fails go to /tmp/mkl and use alien to convert the rpm to a .deb
```
sudo alien --to-deb WHATEVER.rpm
```
then install using dpkg
```
sudo dpkg -i WHATEVER.deb
```

Jeremy

Hey Jeremy, i downloaded the MKL yesterday (8.1.014) and tried to follow your instructions. 

However install.sh doesn't ask me for any folder. Any idea on how to extract the rpms? Installation fails after creating some install32 and installdata files in temp folder, saying 'bash: install32: cannot execute binary file'

Cheers

---

