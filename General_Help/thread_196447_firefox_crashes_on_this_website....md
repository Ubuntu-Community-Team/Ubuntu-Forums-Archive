---
title: "firefox crashes on this website..."
date: 2006-06-14
forum: General Help
---

### Post by c-m on 2006-06-14
everything i visit [www.hexus.net](www.hexus.net), firefox quits.

can anyone shed any light on this at all?

---

### Post by Ramses de Norre on 2006-06-14
Hmm works perfect here.. What flash and java have you installed?

---

### Post by denjin on 2006-06-14
Doesn't crash for me, either.  I have adblock plus, filterset G, and flashblock installed, though.

---

### Post by c-m on 2006-06-14
[QUOTE=Ramses de Norre]Hmm works perfect here.. What flash and java have you installed?[/QUOTE]
none as far as i know, at least none that are working anyway

---

### Post by Trance Gemini on 2006-06-14
works fine for me also.
What FF extensions do you have intalled and what FF ver do you use?

---

### Post by c-m on 2006-06-14
I have version 1.5.0.4 installed, as far as extentions i'm not sure what you are refering to. I only seems to be that one page and happens about 75% of the time

---

### Post by barbarian on 2006-06-14
nice website, btw..

---

### Post by denjin on 2006-06-14
[quote=c-m]I have version 1.5.0.4 installed, as far as extentions i'm not sure what you are refering to. I only seems to be that one page and happens about 75% of the time[/quote]
Go to your tools menu and let us know if anything shows up when you select extensions there.

Also, which flash did you install (if any)?  If you don't know, go into synaptic and search for flash and let us know what it says is installed.  I use the nonfree one.

---

### Post by c-m on 2006-06-14
only extension is the GB language pack.

libflash-mozplugin 0.4.13


carl@carl:~/TransGaming_Drive$ firefox
NP_Initialize
New
SetWindow
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 30 error_code 168 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
carl@carl:~/TransGaming_Drive$

---

### Post by behemot on 2006-06-14
Works OK here.

---

### Post by Christmas on 2006-06-14
I have Kubuntu 6.06 and Firefox 1.5.0.4 and the address works fine, no crash here.

---

### Post by miguelito on 2006-06-14
no crash... but in this page [http://www.chilewarez.cl]("http://www.chilewarez.cl") firefox crash..

i have installed the flash plugins

---

### Post by sugonaut on 2006-06-14
It might be Flash giving you grief.  I had a similar issue a while back.  I installed the 'libflash-mozplugin' package (which depends on the 'libflash0c2' package) at some point.  I uninstalled both and Firefox stopped crashing.

I recommend installing the package, 'flashplugin-nonfree'.  And if you have issues with sound (in Flash movies), check out what worked for me...

[http://www.ubuntuforums.org/showpost.php?p=1138486&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1138486&postcount=11)

Cheers!

---

