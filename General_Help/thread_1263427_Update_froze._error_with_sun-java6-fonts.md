---
title: "Update froze. error with sun-java6-fonts"
date: 2009-09-11
forum: General Help
---

### Post by shiningkenmonster on 2009-09-11
I was updating my system with Update Manager. It was downloading all the packages, than it froze. restarted by hitting the ALT+Print Screen with hitting the keys R+E+I+S+U+B.

than i opened a terminal and typed in:
```

sudo apt-get update
sudo apt-get upgrade

```

it told me to do:
```
sudo dpkg --configure -a
```
to fix the problem.

which i did, it unpack some packages and installed everything correctly. including all the sun-java products which are:

```

sun-java6-bin 
sun-java6-jre 
sun-java6-fonts 
sun-java6-plugin

```

but since this incident happen. I got an error with the sun-java6-fonts:

```
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I used Synaptic Package Manager, looked up sun-java6-fonts, i picked the reinstall box, it reinstalled everything, which are:
```

sun-java6-bin 
sun-java6-jre 
sun-java6-fonts 
sun-java6-plugin

```

than try complete removal and installed again all the sun java packages.

I still keep getting that sun-java6-fonts error. the error still shows up on the command line everytime i do:

```
sudo apt-get autoremove
```

```
kenny@kenny-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ 

```

how do i fix this problem?

---

### Post by brettg on 2009-09-11
Try;

sudo dpkg -r --force-all sun-java6-bin

---

### Post by shiningkenmonster on 2009-09-11
```
kenny@kenny-laptop:~$ sudo dpkg -r --force-all sun-java6-bin
dpkg: sun-java6-bin: dependency problems, but removing anyway as you request:
 sun-java6-plugin depends on sun-java6-bin (= 6-16-0ubuntu1.9.04).
 sun-java6-jre depends on sun-java6-bin (= 6-16-0ubuntu1.9.04) | ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04); however:
  Package sun-java6-bin is to be removed.
  Package ia32-sun-java6-bin is not installed.
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-bin ...
Processing triggers for menu ...
kenny@kenny-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installed
E: Unmet dependencies. Try using -f.
kenny@kenny-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin
The following NEW packages will be installed:
  sun-java6-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/29.1MB of archives.
After this operation, 86.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 135450 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Processing triggers for menu ...
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up sun-java6-bin (6-16-0ubuntu1.9.04) ...

Processing triggers for menu ...
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ sudo dpkg -r --force-all sun-java6-fonts
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-fonts ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
kenny@kenny-laptop:~$ 

```

---

### Post by shiningkenmonster on 2009-09-12
```
kenny@kenny-laptop:~$ sudo dpkg --configure sun-java6-fonts
[sudo] password for kenny: 
Setting up sun-java6-fonts (6-16-0ubuntu1.9.04) ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
kenny@kenny-laptop:~$ 

```

---

### Post by brettg on 2009-09-13
Sorry about delay, timezone differences are a bummer.

It looks like it can't find a file it needs.

Try the following;

touch /etc/defoma/hints/sun-java6-fonts.hints

and then do the apt-get remove again.

---

### Post by shiningkenmonster on 2009-09-13
```
kenny@kenny-laptop:~$ touch /etc/defoma/hints/sun-java6-fonts.hints
touch: cannot touch `/etc/defoma/hints/sun-java6-fonts.hints': Permission denied
kenny@kenny-laptop:~$ sudo apt-get remove sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java6-fonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-fonts ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ 

```

---

### Post by brettg on 2009-09-13
Sorry forgot to mention you will need to be root

sudo touch /etc/defoma/hints/sun-java6-fonts.hints

---

### Post by shiningkenmonster on 2009-09-13
```
kenny@kenny-laptop:~$ sudo touch /etc/defoma/hints/sun-java6-fonts.hints
kenny@kenny-laptop:~$ sudo apt-get remove sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java6-fonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 135819 files and directories currently installed.)
Removing sun-java6-fonts ...
/etc/defoma/hints/sun-java6-fonts.hints: Unable to open, or empty.
dpkg: error processing sun-java6-fonts (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-java6-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kenny@kenny-laptop:~$ 

```

---

### Post by brettg on 2009-09-13
Hmmmm, "Unable to open, or empty."

OK, try putting the following into that file (everything between but not including the lines);

--------------------------------------------

category truetype

# Sans

begin /usr/share/fonts/truetype/ttf-lucida/LucidaSansRegular.ttf
  Family = LucidaSans
  FontName = LucidaSans
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = SansSerif
  Weight = Book
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaSansDemiBold.ttf
  Family = LucidaSans
  FontName = LucidaSans-Demibold
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = SansSerif
  Weight = Bold
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaSansOblique.ttf
  Family = LucidaSans
  FontName = LucidaSans-Oblique
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = SansSerif
  Weight = Thin
  Width = Variable
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaSansDemiOblique.ttf
  Family = LucidaSans
  FontName = LucidaSans-Demibold-Oblique
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = SansSerif
  Weight = Bold
  Width = Variable
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

# Serif

begin /usr/share/fonts/truetype/ttf-lucida/LucidaBrightRegular.ttf
  Family = LucidaBright
  FontName = LucidaBright-Regular
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Roman
  Weight = Book
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaBrightItalic.ttf
  Family = LucidaBright
  FontName = LucidaBright-Italic
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Roman
  Weight = Book
  Width = Variable
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaBrightDemiBold.ttf
  Family = Lucida-Bright
  FontName = Lucida-Bright-Demi
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Roman
  Weight = Bold
  Width = Variable
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaBrightDemiItalic.ttf
  Family = Lucida-Bright
  FontName = Lucida-Bright-DemiItalic
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Roman
  Weight = Demi
  Width = Variable
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

# Mono

begin /usr/share/fonts/truetype/ttf-lucida/LucidaTypewriterRegular.ttf
  Family = LucidaSans-Typewriter
  FontName = LucidaSans-Typewriter
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Typewriter
  Weight = Book
  Width = Fixed
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaTypewriterOblique.ttf
  Family = LucidaSans-Typewriter
  FontName = LucidaSans-Typewriter-Oblique
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Typewriter
  Weight = Book
  Width = Fixed
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaTypewriterBold.ttf
  Family = LucidaSans-Typewriter
  FontName = LucidaSans-Typewriter-Bold
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Typewriter
  Weight = Bold
  Width = Fixed
  Shape = NoSerif Upright
  Foundry = Lucida
  Priority = 15
end

begin /usr/share/fonts/truetype/ttf-lucida/LucidaTypewriterBoldOblique.ttf
  Family = LucidaSans-Typewriter
  FontName = LucidaSans-Typewriter-Bold-Oblique
  Encoding = Unicode
  Location = English
  Charset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-7 ISO8859-9 ISO8859-15
  GeneralFamily = Typewriter
  Weight = Bold
  Width = Fixed
  Shape = NoSerif Oblique
  Foundry = Lucida
  Priority = 15
end

---------------------------------

---

### Post by shiningkenmonster on 2009-09-13
i dont understand. you want me to copy and paste that whole line into the terminal?

---

### Post by brettg on 2009-09-13
OK, sorry

sudo gedit /etc/defoma/hints/sun-java6-fonts.hints 

Copy and paste it into gedit (works just like notepad)

---

### Post by shiningkenmonster on 2009-09-14
thank you! it is fixed. I am just curious. how did you do it?

---

### Post by brettg on 2009-09-14
No problem, glad I could help

No great mystery, just looked at the errors being given and fixed what the script was complaining about.

Whenever you apt-get remove something it runs a remove script. If that script can't finish properly for whatever reason then you end up with something that won't uninstall. It's then just a matter of either fixing whatever it is that is upsetting the script or stopping the script from caring (by editing it) I'm glad we didn't have to go to that step though.

---

