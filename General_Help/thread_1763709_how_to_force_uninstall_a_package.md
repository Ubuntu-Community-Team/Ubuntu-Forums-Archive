---
title: "how to force uninstall a package?"
date: 2011-05-20
forum: General Help
---

### Post by emiller12345 on 2011-05-20
msttcorefonts
Okay, whats up with this? Any other ideas on how to remove it?

```

# apt-get purge -y msttcorefonts 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 201kB disk space will be freed.
(Reading database ... 246035 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

# apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

#  dpkg-reconfigure msttcorefonts
If you have already downloaded Microsoft's TrueType Core Fonts for the web, type the name of the directory which contains them. Those files are in the Microsoft Windows self-installing format, and are named andale32.exe, arial32.exe, arialb32.exe, comic32.exe, courie32.exe, georgi32.exe, impact32.exe, times32.exe, trebuc32.exe, verdan32.exe and webdin32.exe.

If you haven't yet downloaded these fonts, leave this blank and the fonts will be downloaded for you. Approximately 4 MB will need to be downloaded.

If you are not connected to the internet or do not wish to download these fonts now, enter "none" to abort.

Directory holding MS fonts (if already downloaded): none
______
If you need to use a proxy server, please enter it here (example: http://192.168.0.1:8080). This will cause the font files to be downloaded using your proxy. 

Leave this option blank if you don't use a proxy server. 

HTTP proxy to use: 
______
msttcorefonts uses defoma 
Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to  use defoma fonts.

The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.      

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required. 
______
# apt-get install --reinstall msttcorefonts 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of msttcorefonts is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by oldos2er on 2011-05-20
Which version of Ubuntu are you using? On 11.04, the correct package name is ttf-mscorefonts-installer

---

### Post by emiller12345 on 2011-05-20
Ah,sorry, Lucid 10.04
This is an upgrayedd from Hardy 8.04, with a botched wine install.  I really don't want to have to format, thought maybe there was a fix for it.

---

### Post by samMD on 2011-05-20
have you tried running update manager? It worked for me when I had a broken package on my system

---

### Post by emiller12345 on 2011-05-20
yeah, update-manager doesn't recognize and problems at all.  
I even tried installing the newer package ttf-mscorefonts-installer
```

apt-get -y install ttf-mscorefonts-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts
The following NEW packages will be installed:
  ttf-mscorefonts-installer
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/40.2kB of archives.
After this operation, 20.5kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 246035 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Same problem...

---

### Post by oldos2er on 2011-05-21
I've never seen that 'not registered' error, so it's kind of puzzling. Did you happen to notice any errors when you first installed it?

You could try this command: ```
sudo fc-cache -sv
``` and see if it picks up the /usr/share/fonts/truetype/msttcorefonts folder. If it doesn't, try ```
sudo fc-cache -fv
``` which will force it to regenerate your font cache. ```
man fc-cache
``` for more info. I don't know if this will work, but it shouldn't hurt anything.

---

### Post by emiller12345 on 2011-05-21
so here are the results...

```

sudo fc-cache -sv
/usr/share/fonts: skipping, existing cache is valid: 0 fonts, 3 dirs
/usr/share/fonts/X11: skipping, existing cache is valid: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: skipping, existing cache is valid: 84 fonts, 0 dirs
/usr/share/fonts/X11/encodings: skipping, existing cache is valid: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/truetype: skipping, existing cache is valid: 1 fonts, 16 dirs
/usr/share/fonts/truetype/freefont: skipping, existing cache is valid: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: skipping, existing cache is valid: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: skipping, existing cache is valid: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: skipping, existing cache is valid: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: skipping, existing cache is valid: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: skipping, existing cache is valid: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: skipping, existing cache is valid: 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: skipping, existing cache is valid: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: skipping, existing cache is valid: 8 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: skipping, existing cache is valid: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: skipping, existing cache is valid: 4 fonts, 0 dirs
/usr/share/fonts/type1: skipping, existing cache is valid: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: skipping, existing cache is valid: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/texmf/fonts/type1/public/lm: skipping, existing cache is valid: 92 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
fc-cache: succeeded

```

```

sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 84 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 16 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/$USER/.fonts: skipping, no such directory
/usr/share/texmf/fonts/type1/public/lm: caching, new cache contents: 92 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/$USER/.fontconfig: cleaning cache directory
/home/$USER/.fontconfig: invalid cache file: 515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
/home/$USER/.fontconfig: invalid cache file: 26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
/home/$USER/.fontconfig: invalid cache file: a341218890af1fe9ee20256633200406-le32d4.cache-3
/home/$USER/.fontconfig: invalid cache file: 401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
fc-cache: succeeded

```

I've re downloaded the ms fonts from source forge, but they are .exe files, and I can't install wine without msttcorefonts...

When I first installed wine there were no errors, but then I tried to un-install it I got there error above with the fonts.  I bet this is Microsoft's fault some how

---

### Post by oldos2er on 2011-05-21
Well, I'm at a loss to know what to do next. Sorry.

---

### Post by emiller12345 on 2011-05-21
Thank you very much for your help anyway, this has been bugging me for a while, I wasn't expecting an easy answer. I guess I can't use wine ... oh darn ! :)

---

### Post by matt_symes on 2011-05-22
Hi

Have you considered manually removing the package and associated files, using dpkg query tools to get the names of the files used by the package, and the rm command and then trying to reinstall using dpkg and forcing an overwrite ?

If you want to do this and are not sure how then post back.

Kind regards

---

### Post by Spyderkid on 2011-05-22
First do an
sudo apt-get update

then run computer janitor, should be installed on your computer by defualt.

then check if its still there...

then try using the actual synaptic package manager instead of apt-get.

---

### Post by emiller12345 on 2011-05-25
I figured this one out... 
you can't purge this package without the file "/etc/defoma/hints/msttcorefonts.hints"
and this is part of the problem.
```

$ cat /etc/defoma/hints/msttcorefonts.hints
category truetype
begin /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf
  Family = Andale-Mono
  FontName = AndaleMono
  Encoding = Unicode
  Location = Magyar Dutch Spanish Czech Russian English Slovak Catalan Italian Danish Turkish Slovenian Basque Portuguese German Swedish Polish Norwegian French Finnish Greek
  Charset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP437 CP850 CP1251 ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-7 ISO8859-9 ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP437 CP850 CP1251
  GeneralFamily = Typewriter
  Weight = Medium
  Width = Fixed
  Shape = NoSerif Upright
  Foundry = Monotype
  Priority = 20
end
begin /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
  Family = Arial
  FontName = Arial-Regular
  Alias = Helvetica
  Encoding = Unicode
  Location = Magyar Dutch Spanish Czech Vietnamese Russian English Catalan Slovak Italian Turkish Danish Slovenian Basque Portuguese German Polish Swedish Norwegian French Finnish Greek
  Charset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-6 ISO8859-7 ISO8859-8 ISO8859-9 ISO8859-9e ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP437 CP850 CP1251 CP1255 VISCII1.1-1 TCVN-5712 TATAR-CYR ISO10646-1
  UniCharset = ISO8859-1 ISO8859-2 ISO8859-3 ISO8859-4 ISO8859-5 ISO8859-6 ISO8859-7 ISO8859-8 ISO8859-9 ISO8859-9e ISO8859-10 ISO8859-13 ISO8859-14 ISO8859-15 KOI8-R KOI8-U CP437 CP850 CP1251 CP1255 VISCII1.1-1 TCVN-5712 TATAR-CYR
  GeneralFamily = SansSerif....

```
Its this long nasty file with all the windows fonts in it. I edited it so that it looked like this, then removed it.

```

$ cat /etc/defoma/hints/msttcorefonts.hints
category truetype
$ sudo apt-get purge msttcorefonts 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 246178 files and directories currently installed.)
Removing msttcorefonts ...
Purging configuration files for msttcorefonts ...
Processing triggers for fontconfig ...

```
Ha! Thanks Everybody!

---

### Post by kelmark2180 on 2011-05-29
> **matt_symes said:**
> Hi

Have you considered manually removing the package and associated files, using dpkg query tools to get the names of the files used by the package, and the rm command and then trying to reinstall using dpkg and forcing an overwrite ?

If you want to do this and are not sure how then post back.

Kind regards
I would be interested in how to manually rm the package that has a looping bash script, RE:
ii  hylafax-client 2:6.0.3-5.1ubu Flexible client/server fax software - client
iF  hylafax-server 2:6.0.3-5.1ubu Flexible client/server fax software - server

Thanks; Don

---

