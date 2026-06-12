---
title: "Trouble installing game &quot;Wakfu&quot; on Ubuntu"
date: 2012-01-12
forum: General Help
---

### Post by Ecaflip on 2012-01-12
Hello.  I am running Ubuntu 11.10 on a desktop.  I know very little about Linux in general, but I have always been interested in the "open source" movement.  But since I am a gamer as well, I never really invested any time or energy in Linux because they games I wanted to play were always only on Windows, or very rarely Windows/Mac.  

Well that has changed now because the game "Wakfu" by Ankama Games has a Linux version.  If it's available on Linux then I want to try to play it on Linux.  The game ran fine with no problems on Windows, but with Ubuntu the installer does not even launch properly.  The game installer is here (if you are in US/Canada):

[http://www.wakfu.com/na/mmorpg/download](http://www.wakfu.com/na/mmorpg/download)

I am used to just double clicking an installer file and having the installer opening.  For some reason with Ubuntu I am just getting a white screen.  The file wants to open with a program called "gedit."  Is this what I should be using to open this kind of file?  

Can anyone help me get Wakfu running on Ubuntu?  Now, if it's a problem with the game then that's fine, but I have a feeling that the problem is just me not knowing how to use Ubuntu.

Here is the picture of the white box I get when I try to open the installer.

[IMG]http://i40.tinypic.com/v42rup.png[/IMG]

---

### Post by robgill on 2012-01-13
Hi,

The .sh file type is a shell script, so you will not install by double clicking (that is opening in gedit - the text editor).

Instead, you should run it in a terminal.

Navigate to the directory where the file is using cd - for example if it's on your downloads folder:
```
cd ~/Downloads
```

then run the script
```
sh wakfu-installer-linux-na.sh
```

if the installer needs root permissions use sudo.

Hope this helps.

---

### Post by Ecaflip on 2012-01-13
Thank you so much robgill.  I'm sure that's obvious information to most users here but I had no clue that is what I needed to do.  I followed the directions that you gave me but I ran into a problem.  It says that the file is not in gzip format.  What should I do?
Also, I don't know what binary mode is.
Sorry for so many questions but I will be very thankful if I can learn how to install this program.  I don't want to have to go back to Windows.  D:

[IMG]http://i42.tinypic.com/v6ncld.png[/IMG]

---

### Post by cryptotheslow on 2012-01-13
When I visit that download page and hit the Download Wakfu - Linux Version button I end up with a file called "Wakfu_unix.sh"

Where did your wakfu-installer-linux-na.sh come from?


Looking at the install script I ended up with (may or may not be the same as yours!) that error seems to come from here:

```
gunzip sfx_archive.tar.gz
if [ "$?" -ne "0" ]; then
  echo ""
  echo "I am sorry, but the installer file seems to be corrupted."
  echo "If you downloaded that file please try it again. If you"
  echo "transfer that file with ftp please make sure that you are"
  echo "using binary mode."
```


So it just seems to be having a problem unzipping one of the compressed files (from the name of it "sfx" I'd presume the sound files).

Anyway - try deleting what you have and downloading it again first of all.

---

### Post by robgill on 2012-01-14
> **Ecaflip said:**
> Thank you so much robgill.  I'm sure that's obvious information to most users here but I had no clue that is what I needed to do.  I followed the directions that you gave me but I ran into a problem.  It says that the file is not in gzip format.  What should I do?
Also, I don't know what binary mode is.
Sorry for so many questions but I will be very thankful if I can learn how to install this program.  I don't want to have to go back to Windows.  D:


Hi, I just downloaded the file and it seems to install fine for me (the file was the linux-na name like you have). As the above poster said - maybe there is a problem with your original download - try deleting the file and downloading again - I hope it works for you.

BTW - I installed on 11.10.

Edit: I can run the updater - when I try to run the actual game, there seems to be a java architecture problem - I use 64bit 11.10 - maybe someone else will have more info

---

### Post by robgill on 2012-01-15
Can now run Wakfu

The java error was unable to locate unpack200

So in Wakfu/jre/bin

run this to make a symlink 

```
ln -s /usr/bin/unpack200 unpack200
```

Wakfu will run but the text is all boxes (see attached).

Looks like you may be able to find solutions here, but as I won;t be playing Wakfu, I probably won't test it myself.

[http://www.wakfu.com/na/forum/225-linux-support/1437-text-looks-like-boxes](http://www.wakfu.com/na/forum/225-linux-support/1437-text-looks-like-boxes)

You might get good responses there! Good luck!

---

### Post by IanW on 2012-01-15
Text all boxes sounds like it's looking for a font you don't have.

---

### Post by eB0Y on 2012-04-11
Please see [http://ubuntuforums.org/showthread.php?p=11835459#post11835459](http://ubuntuforums.org/showthread.php?p=11835459#post11835459)

for a solution.

It has nothing to do with missing fonts, but with font rendering I think.

---

