---
title: "Installed Fonty Python, Inkscape &amp; put A LOT of fonts on my hard drive,  too slow now"
date: 2012-05-15
forum: General Help
---

### Post by TMundo on 2012-05-15
Hi community:

     I have a Dell Precision 390 with an 80GB hard drive that has Ubuntu 12.04 installed across the entire partition, and a 40GB drive for standard storage. Things were actually pretty good until I connected the 40GB drive that already had the fonts stored on it.  I did transfer the fonts back and forth a few times from the 40GB to the 80GB and back again, I didn't really know the best place to put them, they were in a folder on the Unity Desktop for a while.  There are thousands upon thousands of them.

I also installed Inkscape (graphic design program) and The Fonty Python Font Manager program.  I began putting together font lists and installing them.

It was at this point that I noticed that the computer could no longer handle more than one program at a time.  Even calling up the processes list would not work, it simply would not pop up.  I would eventually shut the whole computer off manually and restart.

Additional info:

Other additional programs installed that did not originally come with Ubuntu include the Screensaver (also kept on my desktop for easy accessibility) and the Compiz Config.  The desktop cube is not activated at the moment.

I initially started all of this in 11.04, and recently upgraded to 12.04.

I have never added more RAM than what initially came with this computer

At one point one of my 40GB drives began to fail, so I transfered everything to the 80GB drive, switched out the 40GB with another one, and then transfered everything back from the 80GB to the new 40GB drive.

Other issues include not being able to put pictures and images back onto the pendrive I got them off of in the first place.  Transferring large pieces of data in one large folder is also a no-no, I cannot even delete info in large quantities, I have to do it one folder at a time.

I want speed, but am assuming I did something stupid when I added the fonts, maybe there are just too many, but I thought keeping them on a separate hard drive would help, on the other hand, maybe that's a bad Idea.

---

### Post by Rodney9 on 2012-05-15
What are the specifications of your machine, cpu , ram etc ?

The ```
df
``` command will show you how much free space you have.

Put just the fonts you wish to use in  a folder in your home directory and name it ```
.fonts
``` then run ```
sudo fc-cache -f -v
``` that will update your font cache and all programs will be able to use them.

Rodney

---

### Post by TMundo on 2012-05-16
After entering code: 

df

into the terminal I get:

tmundo@tmundo-Precision-WorkStation-390:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1       77475256 13619512  59975656  19% /
udev              245516        4    245512   1% /dev
tmpfs             101108      848    100260   1% /run
none                5120        0      5120   0% /run/lock
none              252764       76    252688   1% /run/shm

---

### Post by TMundo on 2012-05-16
Rodney:

     I will put the fonts in the home directory, with the slow issues and trouble transferring things from one place to another it will take some time.  Is there a specific name I must give the folder (will "fonts" simply do?) and should they all be in the same folder or will subdirectories work?  The fonts came as a bunch of different collections, each in their own folder, do I need to combine them all into one?

Thanks for the help

-TMundo

---

### Post by TMundo on 2012-05-16
After entering code: 

df

into the terminal I get:

tmundo@tmundo-Precision-WorkStation-390:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1       77475256 13619512  59975656  19% /
udev              245516        4    245512   1% /dev
tmpfs             101108      848    100260   1% /run
none                5120        0      5120   0% /run/lock
none              252764       76    252688   1% /run/shm

Home directory, I put a folder in there called fonts, and I transfered some of the fonts into it.  I could not name the folder: 

.fonts 

because it said there was already a folder called that.  Entering: 

.fonts 

into the terminal gave me a command not found message

but the code:

[FONT=monospace]sudo fc-cache -f -v

gave me this:
[/FONT]
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 44 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 16 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/kacst: caching, new cache contents: 15 fonts, 0 dirs
/usr/share/fonts/truetype/kacst-one: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao-gothic: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tlwg: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts-core: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/tmundo/.fonts: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/tmundo/.fontconfig: cleaning cache directory
/home/tmundo/.fontconfig: invalid cache file: 5c568772b6f555ec9101966aad8a986b-le32d4.cache-3
fc-cache: succeeded

a little bit faster now too

---

### Post by Rodney9 on 2012-05-23
> a little bit faster now too

Good to hear.

All fonts you add should be in the directory ```
.fonts 
```so the operating system can find them.

Always run ```
sudo fc-cache -f -v
``` when you add new fonts, this updates the operating systems font data base.

If you want more speed you could use a lighter Flavour of Ubuntu like [Xubuntu]("http://xubuntu.org/tour/") or [Lubuntu]("http://lubuntu.net/")

Rodney

---

### Post by TMundo on 2012-05-28
hmmm

I couldn't find the directory .fonts, I know it's there because when I tried to create it it told me the directory already existed, but I cannot get to it, is it hidden due to certain settings.

I appoligize for sounding like such a newbie, but I gotta start somewhere.

---

