---
title: "Bash - No such file or directory"
date: 2011-10-08
forum: General Help
---

### Post by goodvikings on 2011-10-08
Hey everyone

I'm having an issue with bash on a ubuntu 9.10 netbook. I just installed the sun studio compilers and am having an issue running CC (note, not cc but CC)

When I try to run CC, bash gives the error "no such file or directory" but cc runs fine. It's not the PATH becuase it does it even in the right directory with "./CC". Its not something with permissions because its chmod'd 777.

If I try sh or csh instead of bash then it happens for both CC and cc.

Any ideas?

Cheers

Ramo

---Edit---

Cancel that, its now doing it for both CC and cc. Not sure what changed. Still, a massive problem for me

---

### Post by jazzon on 2011-10-08
What is the path that leads to CC?  (as in /usr/bin/CC or what)?
What I am thinking here is a symlink in another location pointing to an older instance of the same one.  Do a ```
which CC
``` and make sure it points out the one you want to execute.  If you are running CC via sudo, then do the which as sudo as well.

Other than that thought, out of my league.

---

### Post by goodvikings on 2011-10-08
Thanks, was a good idea. Kinda embarrassed I didn't think to try it before. Output of the two was:

/etc/sunstudio/sunstudio12/bin/CC
/usr/bin/cc

which explains why cc worked but not '/etc/sunstudio/sunstudio12/bin/cc'

Putting the sunstudio directory to the front of the path then has the following for 'which'

/etc/sunstudio/sunstudio12/bin/CC
/etc/sunstudio/sunstudio12/bin/cc

with

bash: /etc/sunstudio/sunstudio12/bin/CC: No such file or directory
bash: /etc/sunstudio/sunstudio12/bin/cc: No such file or directory

---

### Post by AlphaLexman on 2011-10-08
Actually the command 'which' does not identify if it is a symlink, it only tells the user which file is found first in the path.

Use```
file /etc/sunstudio/sunstudio12/bin/CC
```instead.

---

### Post by goodvikings on 2011-10-08
Well, yeah its a symlink, it goes to /etc/sunstudio/sunstudio12/prod/bin/CC which exists, has correct permissions, etc.

Probably was a silly assumption everyones worked with sunstudio compilers before, kinda thought the above went without saying.....

---

### Post by AlphaLexman on 2011-10-08
Does 'CC' work from the command line but not in the script, or just not at all?

Does:
```
CC --help
```
give any output?

---

### Post by goodvikings on 2011-10-08
Nah it doesn't work at all. All of these have been done outside of a script, so CC --help is the same as CC, ie, no such file or directory

---

### Post by AlphaLexman on 2011-10-08
Don't use the symlink, but the actual file, any errors? 
```
/etc/sunstudio/sunstudio12/[COLOR="Red"]prod[/COLOR]/bin/CC --help
```
If not the symlink is broken.

---

### Post by goodvikings on 2011-10-08
The symlink is fine. Doing /etc/sunstudio/sunstudio12/prod/bin/CC gives the same error.

---

### Post by AlphaLexman on 2011-10-08
What is the output of:
```
shopt | grep nocase
```

---

### Post by goodvikings on 2011-10-08
```

$ shopt | grep nocase
nocaseglob      off
nocasematch     off

```

---

### Post by AlphaLexman on 2011-10-08
I was kinda hoping that was it! I am really shooting in the dark now, but will try to help as much as I can... Try:
```
ls -l /usr/bin/cc /etc/sunstudio/sunstudio12/bin/CC /etc/sunstudio/sunstudio12/prod/bin/CC
```
and post the results

---

### Post by goodvikings on 2011-10-08
Nothing out of the ordinary, I don't think

```

$ ls -l /usr/bin/cc /etc/sunstudio/sunstudio12/bin/CC /etc/sunstudio/sunstudio12/prod/bin/CC
lrwxrwxrwx 1 root root     14 2011-10-08 22:37 /etc/sunstudio/sunstudio12/bin/CC -> ../prod/bin/CC
-rwxrwxrwx 1 root root 409427 2007-07-30 20:45 /etc/sunstudio/sunstudio12/prod/bin/CC
lrwxrwxrwx 1 root root     20 2011-10-08 17:40 /usr/bin/cc -> /etc/alternatives/cc

```

---

### Post by AlphaLexman on 2011-10-08
Let's look at:
```
file /etc/sunstudio/sunstudio12/prod/bin/CC
```

---

### Post by goodvikings on 2011-10-08
```

$ file /etc/sunstudio/sunstudio12/prod/bin/CC
/etc/sunstudio/sunstudio12/prod/bin/CC: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped

```

libs are in the same [sub]directory. There's /etc/sunstudio/lib symlinked to  /etc/sunstudio/sunstudio12/rtlibs

---

### Post by AlphaLexman on 2011-10-08
You may need to re-install the sun studio compiler, I honestly don't know why you are getting the errors you have. Also, check the md5sum of the .deb or .tar.gz file (however you got the download)

Good Luck!

---

### Post by goodvikings on 2011-10-08
I tried reinstalling it twice, and the tar.gz has worked on other machines. Aw well, thanks for trying. Anyone else out there with some ideas?

---

### Post by goodvikings on 2011-10-08
Bumpin

---

### Post by goodvikings on 2011-10-08
Sigh bumping.

Some more information, I spose. Its an asus 101mt, running 9.10.

---

