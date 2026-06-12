---
title: "Problem with cyrillic fonts support"
date: 2011-07-01
forum: General Help
---

### Post by madtyn on 2011-07-01
Hi,

my problem is that I can't extract some files because of a problem with cyrillic fonts (at least, this is what I suspect). 

The point is that I download some kind of files, which are fully functional to extract and open in windows but in Ubuntu trying the same thing, ends with an error.

Files are downloaded from a russian web, so I think the fonts are  cyrillic, which is the root of the problem. In windows they are shown as some kind of rare ASCII string but it's OK to open them.

The problem when trying in Ubuntu is that the file is shown as a large string with question marks '?' replacing all non-latin characters and it may cause problem, as it is the wildcard shell character in Linux. Renaming the file seems as an impossible task too.

I have to process many of these files. Does Anyone know how can I avoid windows to do this?

I tried to install many packages for cyrillic/russian support through synaptic nut it didn't seem to work.

Thank you very much.

---

### Post by prodigy_ on 2011-07-01
> **madtyn said:**
> The problem when trying in Ubuntu is that the file is shown as a large string with question marks '?' replacing all non-latin characters and it may cause problem, as it is the wildcard shell character in Linux. Renaming the file seems as an impossible task too.
You mean these files are supposed to have cyrillic names?

---

### Post by Enigmapond on 2011-07-01
> **madtyn said:**
> Hi,

my problem is that I can't extract some files because of a problem with cyrillic fonts (at least, this is what I suspect). 

The point is that I download some kind of files, which are fully functional to extract and open in windows but in Ubuntu trying the same thing, ends with an error.

Files are downloaded from a russian web, so I think the fonts are  cyrillic, which is the root of the problem. In windows they are shown as some kind of rare ASCII string but it's OK to open them.

The problem when trying in Ubuntu is that the file is shown as a large string with question marks '?' replacing all non-latin characters and it may cause problem, as it is the wildcard shell character in Linux. Renaming the file seems as an impossible task too.

I have to process many of these files. Does Anyone know how can I avoid windows to do this?

I tried to install many packages for cyrillic/russian support through synaptic nut it didn't seem to work.

Thank you very much.


Right...I know what you mean. Have you installed the RU language pack?  If not. Administration->Language Support and make sure it's  installed. As long as it's installed, it will let you see them even if  English is used...

&#1059;&#1076;&#1072;&#1095;&#1080;!

---

### Post by madtyn on 2011-07-02
I've just installed the russian pack using the option in Administration -> Language Support. It doesn't work.

Yes, I think the files' names are in cyrillic characters (it's the most logical thing to think when I see strange symbols/characters in the name from files downloaded from Russian web).

The .zip files are OK in latin with names in latin characters, but the files inside are the ones which cause the problem.

You can try with this short file as example:

[http://notes.tarakanov.net/instrum/barberviolintitul.zip](http://notes.tarakanov.net/instrum/barberviolintitul.zip)

If you can decompress it and open the file inside, just tell me how, please.

---

### Post by prodigy_ on 2011-07-02
It's a known bug in unzip utility:
[https://bugs.launchpad.net/ubuntu/+source/unzip/+bug/580961?comments=all](https://bugs.launchpad.net/ubuntu/+source/unzip/+bug/580961?comments=all)

A workaround:

1) Install convmv package:
```
apt-get install convmv
```

2) Extract all files from archive to an empty folder:
```
unzip archive-name -d folder-name
```

3) Convert filenames:
(This example assumes cp866 as the original filename encoding within archive and utf-8 as Ubuntu locale.)
```
convmv -f iso8859-1 -t cp850 -r --notest --nosmart folder-name/*
convmv -f cp866 -t utf8 -r --notest --nosmart folder-name/*
```

This works with your test archive. Another proposed solution is to install Wine and unpack archives with WinZip (I haven't tested this).

More info here:
[http://www.linuxfromscratch.org/blfs/view/cvs/general/unzip.html](http://www.linuxfromscratch.org/blfs/view/cvs/general/unzip.html)

---

### Post by madtyn on 2011-07-02
Thank you. I will check this tomorrow.

---

### Post by madtyn on 2011-07-04
With the Russian support it seems to work ok to show the files in the shell output.

I didn't need to make the convmv.

From the gnome-file-roller is keeps failing but now I've got an alternative and I can make a script with this.

I will study about the convenience of converting file names with the convmv command.

Thank you all very much for the answer. :p

---

### Post by 3Miro on 2011-07-04
> **madtyn said:**
> I've just installed the russian pack using the option in Administration -> Language Support. It doesn't work.

Yes, I think the files' names are in cyrillic characters (it's the most logical thing to think when I see strange symbols/characters in the name from files downloaded from Russian web).

The .zip files are OK in latin with names in latin characters, but the files inside are the ones which cause the problem.

You can try with this short file as example:

[http://notes.tarakanov.net/instrum/barberviolintitul.zip](http://notes.tarakanov.net/instrum/barberviolintitul.zip)

If you can decompress it and open the file inside, just tell me how, please.

Here is what I did:
- download the file
- right-click and say "extract here", then I got s file with messed up name (something about wrong encoding, the issue is with the file not the fonts).
- right-click on the file and rename it to whatever you want, it opens just fine (some Concerto for Violin ...)

I am using Thunar, but Nautilus should be fine too.

---

### Post by madtyn on 2011-07-04
Yes, you're both right. I tried with file-roller and didn't make it from the GUI, but making with the contextual menu works OK.

And it displays properly, allowing the rename.

The only thing it doesn't work now is the convmv whose output is:


(I paste the three variants I tried and the common part below)
```

cp866 doesn't cover all needed characters for: "./&#1058;&#1080;&#1090;&#1091;&#1083;&#1100;&#1085;&#1099;&#1081; &#1083;&#1080;&#1089;&#1090;, &#1089;&#1086;&#1089;&#1090;&#1072;&#1074; &#1086;&#1088;&#1082;&#1077;&#1089;&#1090;&#1088;&#1072; (2&#1089;&#1090;&#1088;.).tif"

cp850 doesn't cover all needed characters for: "./&#1058;&#1080;&#1090;&#1091;&#1083;&#1100;&#1085;&#1099;&#1081; &#1083;&#1080;&#1089;&#1090;, &#1089;&#1086;&#1089;&#1090;&#1072;&#1074; &#1086;&#1088;&#1082;&#1077;&#1089;&#1090;&#1088;&#1072; (2&#1089;&#1090;&#1088;.).tif"

iso-8859-1 doesn't cover all needed characters for: "./&#1058;&#1080;&#1090;&#1091;&#1083;&#1100;&#1085;&#1099;&#1081; &#1083;&#1080;&#1089;&#1090;, &#1089;&#1086;&#1089;&#1090;&#1072;&#1074; &#1086;&#1088;&#1082;&#1077;&#1089;&#1090;&#1088;&#1072; (2&#1089;&#1090;&#1088;.).tif"

To prevent damage to your files, we won't continue.
First fix this or correct options!

```

But it's no longer necessary since I know how to do it manually and by script.

Thank you all again.

---

