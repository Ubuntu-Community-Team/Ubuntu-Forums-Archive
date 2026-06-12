---
title: "What to do with an AMD64 Static Binary?"
date: 2010-12-14
forum: General Help
---

### Post by colinnwn on 2010-12-14
I'm trying to use the software tool here, using the AMD64 static binary for no other reason than I am trying to install and use it on a 64 bit instance of MythBuntu.
[http://analogbit.com/software/edid_disable_exts](http://analogbit.com/software/edid_disable_exts)

I figured I follow the instructions here
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

But the 64bit version doesn't have a configure file. The only file in there is a .exe, that doesn't do anything when you double click it in a Linux file explorer, and I didn't know you even use .exes on Linux. 

After lots of googling (very little information out there that isn't specific to a software package) it looks like maybe you skip the `configure` and `make`, and go straight to `make install`? Can I do checkinstall instead as recommended on the Ubuntu wiki? 

Or have I got this totally wrong? Is this unnecessary, and I should just use the regular source files on my 64 bit Mythbuntu install?

Thanks.

---

### Post by spcwingo on 2010-12-14
The reason you can't compile it is because it is already compiled (binary).  ;)

---

### Post by colinnwn on 2010-12-14
How do I execute it? As I said it is an .exe file, which I've never heard of using with Linux, though Linux files can have any random name. When I double click it in Thunar file manager, nothing happens.

It is supposed to be a command line utility, that performs some hexidecimal operations on another file (who's name is supplied in the command line). Do I just cd into the folder that contains the .exe and do a -

$ edid_disable_exts.exe --to-dvi my_edid_file

---

### Post by spcwingo on 2010-12-15
You can try running under wine (as it is a windows executable) although I personally would be a bit suspicious.  The reason I say that is:  if you downloaded it with it being labeled as "Linux AMD64 Binary" and instead got a "windows executable binary" it sounds like someone is phishing for random windows users to download and execute.  This, of course, is just my $0.02.

---

### Post by colinnwn on 2010-12-15
Well I've read many reports of people compiling and using the source successfully, but not of using the static binary. 

This utility doesn't make sense in the context of Windows. It is specifically for using with the proprietary Nvidia Linux display driver, to allow you to strip the audio availability information from your extended display identification datastream, so your TV won't think audio is available and play static when connected by HDMI to the Nvidia DVI-D out.

Possibly the site got hacked and the AMD64 bit files got replaced with a windows executable. Or possibly for whatever reason, the author of the file thought naming the Linux program with a .exe would be good.

I'm tempted to try running this .exe from the command line in Linux, and if that doesn't work, try compiling the other file set provided on that website instead.

---

### Post by Wim Sturkenboom on 2010-12-15
Can't one check the first couple of bytes using a hex editor or vi? Should contain the word *ELF* somewhere; might be different for 64 bit.

Below the first block when running (under Slackware 32 bit)
```

vi /bin/sh

```
```

 offset    0  1  2  3   4  5  6  7   8  9  a  b   c  d  e  f  0123456789abcdef
00000000 <7f>45 4c 46  01 01 01 00  00 00 00 00  00 00 00 00  .ELF............
00000010  02 00 03 00  01 00 00 00  a0 b5 05 08  34 00 00 00  ........*µ..4...
00000020  44 27 0a 00  00 00 00 00  34 00 20 00  08 00 28 00  D'......4. ...(.
00000030  1a 00 19 00  06 00 00 00  34 00 00 00  34 80 04 08  ........4...4...
00000040  34 80 04 08  00 01 00 00  00 01 00 00  05 00 00 00  4...............
00000050  04 00 00 00  03 00 00 00  34 01 00 00  34 81 04 08  ........4...4...
00000060  34 81 04 08  13 00 00 00  13 00 00 00  04 00 00 00  4...............
00000070  01 00 00 00  01 00 00 00  00 00 00 00  00 80 04 08  ................
00000080  00 80 04 08  1c c3 09 00  1c c3 09 00  05 00 00 00  .....Ã...Ã......
00000090  00 10 00 00  01 00 00 00  20 c3 09 00  20 53 0e 08  ........ Ã.. S..
000000a0  20 53 0e 08  58 58 00 00  7c a2 00 00  06 00 00 00   S..XX..|¢......
000000b0  00 10 00 00  02 00 00 00  b4 17 0a 00  b4 a7 0e 08  ........´...´§..
000000c0  b4 a7 0e 08  d8 00 00 00  d8 00 00 00  06 00 00 00  ´§..Ø...Ø.......
000000d0  04 00 00 00  04 00 00 00  48 01 00 00  48 81 04 08  ........H...H...
000000e0  48 81 04 08  20 00 00 00  20 00 00 00  04 00 00 00  H... ... .......
000000f0  04 00 00 00  50 e5 74 64  f0 c2 09 00  f0 42 0e 08  ....PåtdðÂ..ðB..

```

---

### Post by dcstar on 2010-12-15
> **colinnwn said:**
> How do I execute it? As I said it is an .exe file, .........

I have no idea why you think it is an .exe file, the one in the download file is simply a file with **no** .exe suffix.

---

### Post by colinnwn on 2010-12-19
> **dcstar said:**
> I have no idea why you think it is an .exe file

Apparently I don't either. I must have been trying to do and remember too many things at once, got frustrated and confused. I've used Linux at the command line off and on for several years, but I still get tripped up when I've been back on Windows for a while. I kept trying to do a -

$ edid_disable_exts --to-dvi my_edid_file_in my_edid_file_out

and getting command not found. Then I realised I probably needed to do a

$ **[COLOR="Red"]./[/COLOR]**edid_disable_exts --to-dvi my_edid_file_in my_edid_file_out

and it worked perfectly. Sorry for the bother.

---

