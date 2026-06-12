---
title: "How to install WinRAR in Ubuntu?"
date: 2009-10-23
forum: General Help
---

### Post by jhb1608 on 2009-10-23
Anyone can suggest me a good unzipping program (includes .rar files, or anything)?

My OS is Ubuntu 9.04.

---

### Post by markusf21 on 2009-10-23
```
sudo apt-get install unrar
``` into terminal. THen file roller can handle rar files

---

### Post by jhb1608 on 2009-10-23
> **markusf21 said:**
> ```
sudo apt-get install unrar
``` into terminal. THen file roller can handle rar files

ok what is file roller?

---

### Post by jeremyswalker on 2009-10-23
I believe it should be at "Applications > Accessories > Archive Manager".

---

### Post by jhb1608 on 2009-10-23
> **jeremyswalker said:**
> I believe it should be at "Applications > Accessories > Archive Manager".

Aha. I don't have Archive Manager.

---

### Post by Bachstelze on 2009-10-24
> **jhb1608 said:**
> Aha. I don't have Archive Manager.

What do you use then?

---

### Post by jhb1608 on 2009-10-24
> **Bachstelze said:**
> What do you use then?

I use file manager.

---

### Post by jhb1608 on 2009-10-24
ok I forgot how to unrar the file, but remember there is also part1.rar, part2.rar, etc...

---

### Post by jhb1608 on 2009-10-24
> **adambrown81 said:**
> Hi
       WinRAR is no doubt one of the most famous compression tools. Many websites upload files to their server by compressing them in a RAR file to save bandwidth and space. WinRAR is a tool made to create and decompress RAR files. You can install WinRAR on Ubuntu (Linux) with just one terminal command. Its usage in Ubuntu is very similar to Windows. You can easily compress and decompress files and folders in Ubuntu using WinRAR.

Correct, but WinRAR isn't free and only I find is trial version forl inux for WinRAR, it is why I'm here :).

---

### Post by rockstarrem on 2009-10-24
I think just rar should work then...

```

sudo apt-get install rar

```

Try that out.

---

### Post by VectorZero on 2009-10-24
> **jhb1608 said:**
> Aha. I don't have Archive Manager.

Hi, you probably do, since it is installed by default. What happens is that it is probably not visible in the menu. Go to [System > Preferences > Main Menu] them select [Applications/Accessories] on the left panel. You will see "Archive Manager" on the right panel; it is probably the 1st item and is probably unchecked. Check the "Show" box and "Archive Manager" will appears in you menu.

Tell me if it helps.

---

### Post by steve161 on 2009-10-24
Install unrar, as suggested in a previous post.  If you have all the parts in one folder, right click on part 1, select extract here, and you should be good to go.

---

### Post by blwizard on 2009-10-24
> **jhb1608 said:**
> Anyone can suggest me a good unzipping program (includes .rar files, or anything)?

My OS is Ubuntu 9.04.

install unrar, rar, and they should allow you to compress and decompress rar files. I think after you install them, your default archive manager should be able to open rar files, but i'm not sure about it. If it doesn't work, just use the command-line, no much hassel.

Also the 7z package in ubuntu repository can handle rar files as well.

---

### Post by ericab on 2009-10-24
> **blwizard said:**
> 
Also the 7z package in ubuntu repository can handle rar files as well.

7zip is the way to go !

---

### Post by bingung99 on 2009-10-24
True....7zip is just as rocking good as  WinRAR

:guitar:

---

### Post by jhb1608 on 2009-10-24
I found out in the hard way, yes unrar works, but also I had to install unrar-nonfree too.

---

### Post by jhb1608 on 2009-10-24
no wait, it is rar and unrar, yes duh me. It works thanks :).

---

### Post by iKonaK on 2009-10-24
I'm surprised that no one mentioned before but there is also peazip ([http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)) witch can also handle .rar files and is free/libre software :P

---

### Post by stryknyner on 2010-03-27
I tryed to download and install this program it doesn't work does someone have a link to download it? Also I have no idea what your talking about install it in the terminal? what does that mean? I'm just a regular person I know nothing about codes.

---

### Post by stryknyner on 2010-03-27
I tryed that pea software that didn't work either. can someone tell me exactly how you install programs I tryed extracting it and I got more folders I extracted all them and clicked every single file nothing works

---

### Post by stlsaint on 2010-03-27
> Also I have no idea what your talking about install it in the terminal? what does that mean? I'm just a regular person I know nothing about codes.

"Regular person"...what does that mean?? We all are regular people...no one is alien i dont think so this statment is more judgemental or stereotypical. To install from terminal means using commands and not "codes". IE: ```
sudo apt-get <package> 
``` so when they say intstall from terminal that means open up a terminal window and use the COMMAND... not code... 
```
sudo apt-get rar
```

---

### Post by stryknyner on 2010-04-05
dude from texas I am new to ubuntu and it is not at all user friendly and half of the software that you can download from the software center or over the net does not work. That is what I was saying and reading these forums are of no help because everyone here assumes that everyone here knows what the heck everyone is talking about. I tryed to do everything in this thread that people wrote to make these programs work nothing they said worked but after an hour of messing with it somehow it worked but what threw me off was  that it does not work like winrar does in windows. in windows you just select a compressed file and right click and you can unzip it peazip does not work  that easily. But anyway it works now. What I mean by I'm a regular person is I have no education in linux whatsoever and I prefer windows but I kept getting viruses and timewarner shut off my internet and charged a ridiculous fee to start it again then i got more viruses and i got shut off again then i payed the fee again but now I run only ubuntu and have had no problems as far as viruses go. and open office is just like microsoft office. but I have not been able to get any online poker program to work on here I tryed installing wine it doesn't work. The other thing that doesn't work is linux version of itunes. but also several other programs that i've downloaded do not work and I can't uninstall them either. other than that linux is pretty cool I will never use windows again it cost me too much already.

---

### Post by Faith95 on 2010-04-13
how do i get 7zip for ubuntu?

---

### Post by Faith95 on 2010-04-13
and @ jhb1608
hey! :) how did you solve your problem? i have some important files in .rar format and i cant seem to unrar them =(

i tried peazip and the command line thingie but it didn't work

---

### Post by 3rdalbum on 2010-04-13
> **Faith95 said:**
> how do i get 7zip for ubuntu?

If you have 7zip-compressed archives, then you can install the "7z" package from Synaptic Package Manager or run this command:

```
sudo apt-get install 7z
```

On Ubuntu, 7zip works as a 'backend' rather than as a GUI program - so after installing the program you can use Ubuntu's default Archive Manager (File Roller) to compress and decompress 7zip files.

If you're after the ability to use RARs, then you would do the same except install the 'unrar' package.

---

### Post by mkvnmtr on 2010-04-13
If you have a default Ubuntu install why not try double clicking on the rar file and see what happens?

---

### Post by ZnoteOT on 2010-05-28
Thanks helpful! :D

---

