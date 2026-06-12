---
title: "Converting .bin file to .db which is in the location file system"
date: 2009-10-29
forum: General Help
---

### Post by Bharath Kumar V on 2009-10-29
Dear Friends,

I am new to Ubuntu. I am in the process of installing Oracle SQL Developer 1.5. For running, Oracle SQL Developer, we need to install the J2SE JDK 5.0. 
I have successfully downloaded the same. 

But, in the installation process I have faced problems and I am seeking your help, suggestions.

While installing  Ubuntu 9.04 Desktop in my laptop I have created the username as bhaarathkumar. The files I have downloaded ( jdk-1_5_0_20-linux-i586.bin)
is saved in /home/bhaarathkumar

as per the SQL Developer's installation procedures, the file (jdk) has to be owned by root only and only from there I can execute the command for converting  .bin to .deb file.

I have copied the flile to file system. I want to convert .bin file to .deb and run which is file system.

How to convert the .bin file to .deb which is in file system? 
How to run the converted .deb file which will be in file system?

Please suggest.

Thanks and regards
Bharath Kumar V

---

### Post by akakingess on 2009-10-29
> **Bharath Kumar V said:**
> Dear Friends,

I am new to Ubuntu. I am in the process of installing Oracle SQL Developer 1.5. For running, Oracle SQL Developer, we need to install the J2SE JDK 5.0. 
I have successfully downloaded the same. 

But, in the installation process I have faced problems and I am seeking your help, suggestions.

While installing  Ubuntu 9.04 Desktop in my laptop I have created the username as bhaarathkumar. The files I have downloaded ( jdk-1_5_0_20-linux-i586.bin)
is saved in /home/bhaarathkumar

as per the SQL Developer's installation procedures, the file (jdk) has to be owned by root only and only from there I can execute the command for converting  .bin to .deb file.

I have copied the flile to file system. I want to convert .bin file to .deb and run which is file system.

How to convert the .bin file to .deb which is in file system? 
How to run the converted .deb file which will be in file system?

Please suggest.

Thanks and regards
Bharath Kumar V

I think you are mistaking 2 seperate things. I believe that in Linux a .bin is like a zip file which will extract to a temp folder and from there you "compile" the software. I don't think there is a way to "convert" it to a .deb, otherwise everyone (including Sun/Java) would have everything nice and easy in a .deb package. I may certainly be mistaken, but I know when I installed JRE I had to "compile" which is not a big deal if you just follow the directions from Sun/Java.

---

### Post by 2ndunit on 2009-10-29
Executing the .bin file that you downloaded will simply extract the Sun JDK on your current path. A better option would be to get the JDK from the Ubuntu repositories. From the terminal, use:

```
sudo aptitude install openjdk-6-jdk
```

or from multiverse:

```
sudo aptitude install sun-java6-jdk
```

btw, neenga tamizha?

---

