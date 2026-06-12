---
title: "Desperately need help with uninstall, help please"
date: 2012-07-24
forum: General Help
---

### Post by theultrahacker on 2012-07-24
I am sorry if the title bothers u, this is my first post, I created an account here for this question please help
ok, let me get to it...

I installed ubuntu 11.10 from windows 7 with wubi installer.
i installed it by extracting the .iso with winrar and running the .exe from Windows Seven :confused: 

which is not the problem...

been a long time, i need to uninstall ubuntu.the problem starts here...

I re-installed Windows 7 couple of times.
[B]now there's no wubi in 'Add or Remove Programs'
[/B]

I know there is an uninstaller in the drive which i installed in, BUT IT SOMEHOW DOESN'T WORK.

please help, really desperate

---

### Post by flipper T on 2012-07-24
are you sure its there?

ran a search for wubi.exe ?

i haven't used windows in years, but is there still a free app called "revo uninstaller", give that a whizz.

given your panicky tone, i can only assume that your user name is ironic.

but good luck anyhows & keep smiling.

---

### Post by theultrahacker on 2012-07-24
i thought like half an hour for my username -_-
then, i kept this name coz when the issue gets fixed, imma hack some wifi :3 :P
btw thanx

---

### Post by flipper T on 2012-07-24
some more considered thoughts...

you have reinstalled win7 several times?

wubi allows ubuntu to be run as any other app, within a windows environment.

any reinstall of windows would have obliterated any trace of ubuntu.

mmm...something not quite right here

---

### Post by Cheesemill on 2012-07-24
If you have re-installed Windows then you will have already deleted your Ubuntu installation.

Because Wubi stores the Ubuntu files in C:\ubuntu\disks\root.disk then it would have been erased when you re-installed Windows.

If you told Wubi to install to a different location then just delete the relevant root.disk file to uninstall

---

### Post by Frogs Hair on 2012-07-24
Wubi installs Ubuntu inside the Windows partition and Ubuntu runs independently of Windows , but it does use the Windows boot loader. See Cheesemill's post I was about to write the same thing.

---

### Post by theultrahacker on 2012-07-24
sorry if i did something wrong, supern00b here
{despite my nickname}
thanks chesemill, i ll try what u said

---

### Post by theultrahacker on 2012-07-24
okay, the 'ubuntu' in boot menu didnt gtfo'd
wen i click it, it says **cant load coz of corrupted file, repair ur computer by running win7 installation disk and ******

Error code: 0x00000c or sth

---

