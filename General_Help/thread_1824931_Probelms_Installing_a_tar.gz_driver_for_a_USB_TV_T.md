---
title: "Probelms Installing a tar.gz driver for a USB TV Tuner"
date: 2011-08-14
forum: General Help
---

### Post by BrownWarrior on 2011-08-14
[FONT=Times New Roman, serif][SIZE=3]Hi[/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]I'm really struggling to get a usb TV decoder (dvb),  [AVerTV Hybrid Volar HD (H830)]("http://www.avermedia.com/avertv/product/productdetail.aspx?id=501&tab=APDriver") ,  working with ubuntu 11.04. The link provides some text and a 'Linux x86' driver – a .tar.gz file.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Here's an excerpt from the text file [/SIZE][/FONT] 
 

 [FONT=Times New Roman, serif][SIZE=3]*'0. Prerequisits*[/SIZE][/FONT] 
    *a. support linux kernel 2.6.29 or later.*          *Note:*       *1. This package is tested with MythTV against Ubuntu 10.04*       *2. This package is tested with VLC v1.1.4 against Ubuntu 10.04, 10.10 and 11.04*       *3. This package is tested with mplayer and Kaffeine against Ubuntu 10.04 and 10.10* 

     *b. make sure /lib/modules/`uname -r`/build exists* 

*c. make sure "dvb_frontend.h" exist in your Ubuntu.* 

*d. kernel modules dependency: videodev, videobuf-core, v4l2-common, videobuf-vmalloc,*        *dvb-core, i2c-core, tda18271, snd_pcm, snd_timer, snd_page_alloc, snd, soundcore          *  [I]1. 

Install driver to system[/I]      *$ sudo ./xxx_LinuxDrv_x86_vxxx-beta_Install.sh* '

[FONT=Times New Roman, serif][SIZE=3]Here's a list of my problems that I'd like some help with please, if possible.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Going through these points (a) to (d),  I found  my kernel seems suitable (used 'uname -a', and got  2.6.38-10-generic #46).  Likewise, my ubutnu seems acceptable,. [/SIZE][/FONT] 
 [FONT=Times New Roman, serif][SIZE=3]For (b), I seem to have that path - /lib/modules/`uname -r`/build,[/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]For (c), I don't know what ' in your Ubuntu' means. I can google that file, 'dvb_frontend.h', but can't seem to access it or execute it at the terminal. If I'm to download it as a script, where should it be placed, and should it be made executable.[/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]Not sure what to do about (d).[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Needless to say, the last instruction doesn't work 
Install driver to system
$ sudo ./xxx_LinuxDrv_x86_vxxx-beta_Install.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]...though I wouldn't expect it to work, as I'm not sure which path name I should unpack my .tar.gz file in.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Sorry there's so many questions, but I'm hoping they'll all be simple and quick to address.[/SIZE][/FONT]

---

### Post by WyleECoyote on 2011-08-14
to find the file they speak of, open terminal and and execute this command:

$ sudo find / -name 'dvb_frontend.h'
that will see if it exists in your Ubuntu install. if not you have to install the package that holds that file. 

as far as the kernel modules not sure if they are loaded you can try: 
$ lsmod
to list all running modules to see if they exist if not then you can:
$ insmod missingmodulenamehere
if that fails you will need to find the missing modules and install them.

You may also need to install the kernel headers for your running kernel. should be named something like linux-headers-something

the last command, you can unpack the tar.gz anywhere you like as long as you can change the directory to where it is in the terminal. I always suggest everyone install nautilus-open-terminal it gives you right-click access to wherever you are in nautilus to the terminal. then you type:
$ ls
to show the files you should have a file named something like xxx_LinuxDrv_x86_vxxx-beta_Install.sh whatever it is replace it in the command you posted.

---

### Post by BrownWarrior on 2011-08-14
Thanks WyleECoyote

I've now found dvb_frontend.h thanks to you.

Likewise, I now know which modules I'm missing. I'll have to find some of these (e.g., 
videodev). 

I'll then try the last step.

Cheers


[]("http://ubuntuforums.org/member.php?u=434900")

---

### Post by WyleECoyote on 2011-08-14
Your welcome, and good luck it may be a lot of trial and error but everything in linux is worth learning about. Just a hint, the more time you spend in the console running programs the more you will learn about Linux. The console will spit out more info on what could be the issue and in most cases you can copy and paste into google search where you will learn much much more.

---

