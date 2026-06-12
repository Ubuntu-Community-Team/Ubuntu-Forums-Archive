---
title: "Bastion shows no graphics"
date: 2012-06-02
forum: General Help
---

### Post by YongQing on 2012-06-02
Hi all

I installed Bastion using Ubuntu Software Centre. I'm running Xubuntu 12.04.

When I run Bastion, after the WB & developer logos appear, I get a black blank screen with just the music. I can see the cursor and move it. If I move the cursor over where the menu buttons are supposed to be, I can hear the distinct "click" sounds.

Anyone know what is wrong?

---

### Post by Mike_IronFist on 2012-06-03
> **YongQing said:**
> Hi all

I installed Bastion using Ubuntu Software Centre. I'm running Xubuntu 12.04.

When I run Bastion, after the WB & developer logos appear, I get a black blank screen with just the music. I can see the cursor and move it. If I move the cursor over where the menu buttons are supposed to be, I can hear the distinct "click" sounds.

Anyone know what is wrong?

Bastion and Psychonauts both have this problem - they use S3tc textures and for some reason Intel graphics cards don't use these automatically on Linux.

The fix is not very hard though.

Open a terminal enter the following:
```
gksudo echo "force_s3tc_enable=true /opt/Bastion/Bastion.bin.x86_64" > /opt/Bastion/Bastion.sh
gksudo chmod a+x /opt/Bastion/Bastion.sh
```

Then, once that's done, you need to fix the menu launcher to use **Bastion.sh**.

In the terminal, enter the following:
```
gksudo gedit /usr/share/applications/Bastion.desktop
```

(This will use gedit to open Bastion.desktop. In Xubuntu, replace **gedit** with **mousepad**.)

In that file, change **Bastion.bin.x86_64** to **Bastion.sh** Save the file and close and you're done. Bastion should load up with no black screen.

---

### Post by ubusou on 2012-06-03
I had same problem with this game (Ubuntu 12.04, Ati 6450).
This work's for me.

```
sudo apt-get install libtxc-dxtn-s2tc0
```

---

### Post by BantamD5 on 2012-06-03
Ubusou this works! (but no sound...) awesome. any ideas why the sound is missing now?...

---

### Post by tg0bar on 2012-06-04
Mike_IronFist way worked for me like a charm (ubuntu 12.04 amd64 with Intel card). However my Bastion files were not installed in /opt but in /usr/local/games so I had to change the commands to reflect that.

---

### Post by electragician on 2012-06-04
> **ubusou said:**
> I had same problem with this game (Ubuntu 12.04, Ati 6450).
This work's for me.

```
sudo apt-get install libtxc-dxtn-s2tc0
```


This also worked for me on Xubuntu 12.04 32bit. No other tweaks necessary and sound still worked fine.

---

### Post by amedrano on 2012-06-04
This worked for me.

---

### Post by Lord Burghley on 2012-06-04
> **ubusou said:**
> I had same problem with this game (Ubuntu 12.04, Ati 6450).
This work's for me.

```
sudo apt-get install libtxc-dxtn-s2tc0
```

Worked like a charm for me. (Ubuntu 12.04, Mobile Intel HD chipset). Thanks!! ):P

---

### Post by Mr.Gosh on 2012-06-05
Perfekt - That worked for me too (Intel Core i7 Graphics 3000).

Why is this dependancy missing on the packages and how did you come to the idea that this is the right package? :P

---

### Post by Ryanl93 on 2012-06-08
Hi Guys

I tried to follow mike_iron_fists instructions. I noticed that in the instruction it says for xubuntu. I am running Ubuntu 12.04 and when i run the first entry for terminal, it says that the directory doesn't exist.

I then tried to change the directory part of his suggested entry to this :
gksudo echo "force_s3tc_enable=true /opt/Bastion/Bastion.bin.x86_64" > /usr/share/applications/Bastion.sh

When i enter this its says "Bash: bash: /usr/share/applications/Bastion.sh: Permission denied"

What am i doing wrong ?

---

### Post by scottsaysmoo on 2012-06-08
mike_iron_fists solution worked like a charm for me in Ubuntu 12.04.  Bastion was installed to usr/local/games as well.  Make sure that you change both instaces of "opt/" to "usr/local/games" so that your code will look like 

```
gksudo echo "force_s3tc_enable=true /usr/local/games/Bastion/Bastion.bin.x86_64" > /usr/local/games/Bastion/Bastion.sh
```

Followed by

```
gksudo chmod a+x /usr/local/games/Bastion/Bastion.sh
```

and finally

```
gksudo gedit /usr/share/applications/Bastion.desktop
```

Worked like a charm for me!

Thanks, mike!

---

### Post by drumgod on 2012-06-12
When I tried to run sudo apt-get install libtxc-dxtn-s2tc0 my terminal showed that there was no package in existence. Help?

---

### Post by jonaternet on 2012-06-26
@[drumgod]("http://ubuntuforums.org/member.php?u=1673053") : check your software sources e.g open software center / edit /software sources. You can safely enable all the software sources there, except cdrom, otherwise you will have to put your cd every time you wan to install something.... 
Then you might be able to install it, and then the game normally works.
In the worse case, the other trick in first page works too ( or, you can also  launch the game with the command : 
```
force_s3tc_enable=true /usr/local/games/Bastion/Bastion.bin.`uname -p`    
```
it does the same )

---

### Post by sienile on 2012-07-24
> **ubusou said:**
> I had same problem with this game (Ubuntu 12.04, Ati 6450).
This work's for me.

```
sudo apt-get install libtxc-dxtn-s2tc0
```

FINALLY! This was the last thing I needed to get it working. Here's what all I had to do:

[LIST]
[*]Allow RWX to Bastion install directory (/usr/local/games/Bastion)
[*]Edit OpenTK.dll.config
  <dllmap os="linux" dll="libX11" target="libX11.so.6"/>
  <dllmap os="linux" dll="libXi" target="libXi.so.6"/>
[*]sudo apt-get install libtxc-dxtn-s2tc0
[/LIST]

My sound works fine, not sure what's causing BantamD5's issue.

BTW, I'm on Ubuntu Precise x64 with Radeon X2600 PRO.

---

### Post by DaniVS on 2012-11-02
> **ubusou said:**
> I had same problem with this game (Ubuntu 12.04, Ati 6450).
This work's for me.

```
sudo apt-get install libtxc-dxtn-s2tc0
```

This worked for me as well (I have Ubuntu 12.04-32bit on ACER Aspire 3810T)

Thank you very much ubusou!!!

---

### Post by jkms on 2013-05-12
> **jonaternet said:**
> @[drumgod]("http://ubuntuforums.org/member.php?u=1673053") : check your software sources e.g open software center / edit /software sources. You can safely enable all the software sources there, except cdrom, otherwise you will have to put your cd every time you wan to install something.... 
Then you might be able to install it, and then the game normally works.
In the worse case, the other trick in first page works too ( or, you can also  launch the game with the command : 
```
force_s3tc_enable=true /usr/local/games/Bastion/Bastion.bin.`uname -p`    
```
it does the same )

On 64bit with Steam I first needed to rename:
$HOME/.local/share/Steam/SteamApps/common/Bastion/Linux/Bastion.bin.x86
to:
$HOME/.local/share/Steam/SteamApps/common/Bastion/Linux/Bastion.bin.x86_64

And then change the path in the command as per below:
force_s3tc_enable=true $HOME/.local/share/Steam/SteamApps/common/Bastion/Linux/Bastion.bin.`uname -p`



And then it works, thanks!

---

