---
title: "Unpacking .gtgz file"
date: 2009-12-30
forum: General Help
---

### Post by nabeels on 2009-12-30
Hello
Can anyone tell me how to extract a file with gtgz extension?
I tried both:
tar xzvf OpenFOAM-1.6.General.gtgz & tar xvfo OpenFOAM-1.5.General.gtgz
but none success. The following error message is obtained:
tar: Exiting with failure status due to previous errors
Regards
Nabeel

---

### Post by taurus on 2009-12-30
What does it say when you run this command from a terminal?

```
file OpenFOAM-1.6.General.gtgz
```
Where did you download OpenFOAM-1.6.General.gtgz anyway?

---

### Post by nabeels on 2009-12-30
> **taurus said:**
> What does it say when you run this command from a terminal?

```
file OpenFOAM-1.6.General.gtgz
```Where did you download OpenFOAM-1.6.General.gtgz anyway?

abeels@nabeels-laptop:~/OpenFOAM$ file OpenFOAM-1.6.General.gtgz
OpenFOAM-1.6.General.gtgz: gzip compressed data, from Unix, last modified: Mon Jul 27 09:16:29 2009

I copied the file to a directory called OpenFOAM

---

### Post by nabeels on 2009-12-30
> **taurus said:**
> What does it say when you run this command from a terminal?
 
```
file OpenFOAM-1.6.General.gtgz
```
Where did you download OpenFOAM-1.6.General.gtgz anyway?
I downloaded it in a directoy called "Downloads" then copied it to another directory called "OpenFOAM" where it was unpacked!

---

### Post by taurus on 2009-12-30
> **nabeels said:**
> I downloaded it in a directoy called "Downloads" then copied it to another directory called "OpenFOAM" where it was unpacked!

Where means the _site_, not where you saved or moved it to.

---

### Post by nabeels on 2009-12-30
> **taurus said:**
> Where means the _site_, not where you saved or moved it to.
 
sorry for missunderstanding you
this the website I used:
[http://www.opencfd.co.uk/openfoam/linux64.html](http://www.opencfd.co.uk/openfoam/linux64.html)
Thank you for your collaboration

---

### Post by jamesisin on 2009-12-30
I use 7zip for archiving functionality.  You may want to try it.

[http://www.soundunreason.com/InkWell/?p=450](http://www.soundunreason.com/InkWell/?p=450)

---

### Post by taurus on 2009-12-30
From a terminal, navigate to OpenFOAM directory.  Then, unpack it with

```
tar xvzf OpenFOAM-1.6.General.gtgz
```
That would create a new directory, OpenFOAM-1.6 so you need to change to that new directory and have a look at the REAMDE.

```
cd OpenFOAM-1.6
more README
```
Hit the Space key for the next 24 lines.

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> I use 7zip for archiving functionality.  You may want to try it.

[http://www.soundunreason.com/InkWell/?p=450](http://www.soundunreason.com/InkWell/?p=450)

Thank you for the instructions given. However, it failed as the end due to the following message:
[COLOR=Red]tar: OpenFOAM-1.6/doc/Doxygen/html/classFoam_1_1compressible_1_1RASModels_1_1mutSpalartAllmarasStandardRoughWallFunctionFvPatchScalarField_51218d13afa96ba17d82cdeee1f2b25a_icgraph.md5: Cannot open: File name too long
[/COLOR][COLOR=Black]The above message has been repeated for a no. of files?
any idea?

[/COLOR]

---

### Post by taurus on 2009-12-30
Looks to me like you have a bad download.  Remove the current version on your machine and download it again.

I didn't have any problem unpacking it on my machine.

---

### Post by nabeels on 2009-12-30
> **taurus said:**
> Looks to me like you have a bad download. Remove the current version on your machine and download it again.
 
I didn't have any problem unpacking it on my machine.
 
I will do sir, but are you using ubuntu 9.10?

---

### Post by taurus on 2009-12-30
Yes, x86 version.

---

### Post by jamesisin on 2009-12-30
Judging from the error you received, it's a problem with the archive itself.  I was able to download and unzip it here.  Go with the above and try re-downloading it.

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> Judging from the error you received, it's a problem with the archive itself.  I was able to download and unzip it here.  Go with the above and try re-downloading it.

Still the same problem is persisting with the file OpenFOAM-1.6.General.gtgz
I had no problem with unpacking the ThirdParty file, could it because I didn't permit the Update manger?

---

### Post by jamesisin on 2009-12-30
> **nabeels said:**
> I had no problem with unpacking the ThirdParty file, could it because I didn't permit the Update manger?

What?

I don't follow this at all.  What third party file?  How does the archive relate to the update manager?

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> What?
 
I don't follow this at all. What third party file? How does the archive relate to the update manager?
[COLOR=black][FONT=Verdana]In the link I provided, there are two general files:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][OpenFOAM-1.6.General.gtgz]("http://downloads.sourceforge.net/foam/OpenFOAM-1.6.General.gtgz?use_mirror=mesh") and [ThirdParty-1.6.General.gtgz]("http://downloads.sourceforge.net/foam/ThirdParty-1.6.General.gtgz?use_mirror=mesh")  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Of course, I need to unpack both files to be able to install openfoam. The error message I posted above is obtained whenever I unpack [OpenFOAM-1.6.General.gtgz]("http://downloads.sourceforge.net/foam/OpenFOAM-1.6.General.gtgz?use_mirror=mesh"). For the other file, i.e. [ThirdParty-1.6.General.gtgz]("http://downloads.sourceforge.net/foam/ThirdParty-1.6.General.gtgz?use_mirror=mesh") , I could unpack it successfully with no error message.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]For the second part which is related to Update manager, the "Update manager" window is popped out whenever I start ubuntu asking for permitting some components and I just ignore it. I'm just wondering if my OS has a bug which I need to fix in the update![/FONT][/COLOR]
P.S. I'm refusing the update because I don't wanna to get into the grub problems
Nabeel

---

### Post by jamesisin on 2009-12-30
> **nabeels said:**
> For the second part which is related to Update manager, the "Update manager" window is popped out whenever I start ubuntu asking for permitting some components and I just ignore it. I'm just wondering if my OS has a bug which I need to fix in the update![/FONT][/COLOR]
P.S. I'm refusing the update because I don't wanna to get into the grub problems
Nabeel

Run your updates?  You can always specifically exclude Grub.

Which method are you using to extract from this archive?  I was not able to extract using the Archive Manager.  I was able to extract using 7zip.

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> Run your updates? You can always specifically exclude Grub.
 
Which method are you using to extract from this archive? I was not able to extract using the Archive Manager. I was able to extract using 7zip.
I used both: 
tar  xzf <filename>                    and             tar xvfo <filename>

---

### Post by taurus on 2009-12-30
Make sure you unpack one file at a time instead of doing both on the same line.

---

### Post by jamesisin on 2009-12-30
Just to recap, you have run 7z x OpenFOAM-1.6.General.gtgz -o/home/[username]/Desktop

This yielded an archive called OpenFOAM-1.6.General.

When you attempted to run tar xvf OpenFOAM-1.6.General you ran into errors.

Can you post the output (or maybe just the last segment of it) into a code box?

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> Just to recap, you have run 7z x OpenFOAM-1.6.General.gtgz -o/home/[username]/Desktop

This yielded an archive called OpenFOAM-1.6.General.

When you attempted to run tar xvf OpenFOAM-1.6.General you ran into errors.

Can you post the output (or maybe just the last segment of it) into a code box?

Some of the packing inf.

OpenFOAM-1.6/etc/apps/paraview/bashrc
OpenFOAM-1.6/etc/aliases.sh
OpenFOAM-1.6/etc/thermoData/therm.dat
OpenFOAM-1.6/etc/thermoData/BurcatCpData
OpenFOAM-1.6/etc/bashrc
OpenFOAM-1.6/.build
tar: Exiting with failure status due to previous errors

the error is related to some files with long names; can't be opened

---

### Post by jamesisin on 2009-12-30
> **nabeels said:**
> the error is related to some files with long names; can't be opened

Can we see the section that talks about that, please?

You can create a code box by placing CODE and /CODE in square brackets surrounding your code.  There is also a button in the comment editor for doing just this (it has a #).

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> Can we see the section that talks about that, please?

You can create a code box by placing CODE and /CODE in square brackets surrounding your code.  There is also a button in the comment editor for doing just this (it has a #).

I used: script <file name>
then I unpacked the folder again and finally exit;
Some of the error messages (three of them):
[COLOR=Red]tar: OpenFOAM-1.6/doc/Doxygen/html/classFoam_1_1compressible_1_1RASModels_1_1mut
SpalartAllmarasStandardRoughWallFunctionFvPatchScalarField_51218d13afa96ba17d82c
deee1f2b25a_icgraph.md5: Cannot open: File name too long[/COLOR]

[COLOR=Red]tar: OpenFOAM-1.6/doc/Doxygen/html/classFoam_1_1incompressible_1_1RASModels_1_1n
utSpalartAllmarasStandardWallFunctionFvPatchScalarField_656a897e714e1cefeb22bcfa
097e8e30_icgraph.map: Cannot open: File name too long[/COLOR]

[COLOR=Red]tar: OpenFOAM-1.6/doc/Doxygen/html/classFoam_1_1incompressible_1_1RASModels_1_1n
utSpalartAllmarasStandardRoughWallFunctionFvPatchScalarField_fdeceecb1c75e9ccc98
c2f489fe8fa00_cgraph.png: Cannot open: File name too long[/COLOR]


Nabeel

---

### Post by jamesisin on 2009-12-30
Does anyone know of a file name or path length restriction in 9.10?

I was able to parse these files on my system without issue (following the exact same method).

---

### Post by oldos2er on 2009-12-30
> **jamesisin said:**
> Does anyone know of a file name or path length restriction in 9.10?



Depends on which file system is in use.

---

### Post by nabeels on 2009-12-30
> **oldos2er said:**
> Depends on which file system is in use.
 can you elaborate more???!

---

### Post by jamesisin on 2009-12-30
Which files system are you using on the destination drive?

---

### Post by nabeels on 2009-12-30
> **jamesisin said:**
> Which files system are you using on the destination drive?

It is 


[FONT=times new roman][COLOR=#000000]extended 0x05[/COLOR][/FONT]

---

### Post by oldos2er on 2009-12-30
Is it ext3 or ext4? If so, you can probably rule that out as a cause of the problem.

---

### Post by nabeels on 2009-12-30
> **oldos2er said:**
> Is it ext3 or ext4? If so, you can probably rule that out as a cause of the problem.
to what option, there is a big list!
it is now: Linux (0x83)

---

### Post by jamesisin on 2009-12-31
That is one of the extended file systems (I don't recall if it's 3 or 4) and should not be posing the problem you are seeing.  I hope that someone else has some advice about this file name length issue, because I'm a little at a loss.

---

