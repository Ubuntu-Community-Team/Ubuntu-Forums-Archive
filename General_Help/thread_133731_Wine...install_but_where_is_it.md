---
title: "Wine...install but where is it?"
date: 2006-02-20
forum: General Help
---

### Post by kelloggsx on 2006-02-20
Hey all,

After running Automatix and installing wine ( still till this point not 100% sure what it is...)   I did a bit of research and and learn that "wine" should allow you to run "some windows" apps such as ie/office/etc.

Now...couple of questions,

1) how do i verify that "wine" is install and running correctly?
2) where can i find instructions in how-to install ms-office or any other windows app in my ubuntu desktop/laptop?
3) do i have to partition the drive? dual boot ( linux/win )?

or do you guys suggest for me to just install VM and install my M$ stuff there?

Details suggestions are always welcome :)

thanks in advance

---

### Post by hegenious on 2006-02-20
1) when installing wine (windows-emulator) thru automatix, you are warned to run winecfg afterwards. that will setup a local windows tree.

2) google, manpage, wine homepage to name a few

3)no

> or do you guys suggest for me to just install VM and install my M$ stuff there?


this guy does...   :]]   vmware rules

---

### Post by smokinfish on 2006-02-20
i've so far not been able to install anything successfully with wine, never mind make anything appear on the "start menu" for want of a better phrase! 

please tell, what is VM ?

---

### Post by SWAT on 2006-02-21
you can install Wine with "sudo apt-get install wine" or you can try compiling and installing the newest version from their sources.
Checking if wine is installed can be done by "wine -v" which gives you the current wine version.
IMHO DO NOT use Automatix

---

### Post by akiro.yamamoto on 2006-02-21
Configure wine:
<ALT>+<F2>    This will bring up the Run Dialog.
TYPE:
winecfg
This should bring up the WINE Configuration Dialog.
Ensure that your CDRom Drive is detected, Highlight it and click on Show Advanced, then set the type as CD-ROM. ( I had some issues with this setting and DVD Decrypter)
Basically that should be it ;)
Normally everything should be set-up for you at this point. Some Apps may require certain configuration settings for them to work. Check Frank's Corner, TransGaming, WineHQ or Google for any extra setting the app you want to install
may need.
For example DVD Decrypter needs wine to be set as Win NT 4.0 in order to work.
However DVD Shrink needs no extra setting to function and can use the default settings (WINE => 0.93).
Your programs will be install to 
/home/user.name/.wine/drive_c/Program Files (By Default)
To view this directory Open your Home Folder.
Then Click 
View > Show Hidden Files.
You should now be able to see the .wine directory in your home folder.
Check it out and see that the app you wanted to install is actually there.
Post back with any specific problems you have and be as systematic as possible.
NOTE: I used the wine .deb package from WineHq so YMMV ;)

---

