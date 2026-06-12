---
title: "[Lossless] Ripping DVDs to Matroska (MKV)"
date: 2012-04-24
forum: General Help
---

### Post by twipley on 2012-04-24
I am triying to transfer a small collection of DVDs, without losing anything in quality, to the hard drive. Here is what I have came up at, although there seems to be a problem in that no subtitle streams at all get worked with using mkvmerge.

(As a rule, would be desired in the output are the video stream, original-language studio audio, and soft-coded, bitmap-type, English subtitles.)

> install applications: sudo apt-get install libdvdread4 mplayer mkvnixtools & sudo /usr/share/doc/libdvdread4/install-css.sh

ripping all of video, audio, and subtitles, contained in the first title: mplayer dvd://1 -dumpstream -dumpfile <rippedfile>

to have a look at the details of audio and subtitle streams featured on the ripped file: mplayer rippedfile -v

identify which audio and video tracks are contained inside the ripped file: mkvmerge -i <rippedfile>

build mkv with desired tracks: mkvmerge -o <output.mkv> -a <audiotrackid> -d <videotrackid> -s <subtitletrackid> <rippedfile>

I am willing to update the quote field with any hints, tips, or fixes, one might provide.

Notes: (1) mplayer decrypts files on the fly while ripping them, I believe.

(2) One needs not to separately install libdvdread4, as mplayer installs it by default.

---

### Post by SeijiSensei on 2012-04-24
Why don't you just use [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases")?  You can encode to MPEG2, the same codec as the DVD uses, though I bet you'd be hard-pressed to discern a difference between that and H.264 which is the default.

---

### Post by twipley on 2012-04-24
> **SeijiSensei said:**
> Why don't you just use [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases")?  You can encode to MPEG2, the same codec as the DVD uses,
Well, I guess I could. But then, I already have done most of the way using the posted apps, and I think using the CLI looks cool.

> **SeijiSensei said:**
> though I bet you'd be hard-pressed to discern a difference between that and H.264 which is the default.
Actually, I have been meaning to encode using HEVC when it goes out, but have recently chosen to go the way of lossless transferring. Besides, I have chosen to go with DVDs instead of with Blu-ray, because few movies I own (which are mostly *old* movies, by the way) really gain from it. In fact, most, through my own taste standards, suffers from it. An exception to this rule is Casablanca, which seems successful on Blu-ray.

---

### Post by techsupport on 2012-04-25
My suggestion would be either Acid Rip or DVD::Rip (they are located down the following list) :

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

> **twipley said:**
> I am triying to transfer a small collection of DVDs, without losing anything in quality, to the hard drive. Here is what I have came up at, although there seems to be a problem in that no subtitle streams at all get worked with using mkvmerge.

(As a rule, would be desired in the output are the video stream, original-language studio audio, and soft-coded, bitmap-type, English subtitles.)



I am willing to update the quote field with any hints, tips, or fixes, one might provide.

EDIT: Also, mplayer decrypts files on the fly while ripping them, I believe.

---

### Post by twipley on 2012-04-26
Ultimately, it seems that it is MakeMKV combined with mkvmerge GUI that is doing the job the way I am wanting it to be done.

restricted-extras (featuring the MPEG-2 decoder) is to be installed. Suggestion steps for installing MakeMKV (beta) and mkvmerge:

> # first off, download both the binary and the source packages
# over at:	[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

# then, this script file, placed into the same folder as downloaded package files, is to be "ran in terminal;"

sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev

tar -xf makemkv*oss.tar.gz && tar -xf makemkv*bin.tar.gz

cd ./makemkv*_oss
make -f makefile.linux && sudo make -f makefile.linux install

cd ../makemkv*_bin
make -f makefile.linux && sudo make -f makefile.linux install

cd ..
sudo rm -r makemkv*_oss && sudo rm -r makemkv*_bin


> # run the following line from the terminal (ctrl-alt-t):	sudo gedit /etc/apt/sources.list && exit
# then, add the two following text lines to the end of the therefore-opened text file:

deb [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./
deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) ./

# then, open this file this time not using the "display," but the "run in terminal" button;
# take care, though, to input the account password moments after having opened this file that way;

wget -O - [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt) | sudo apt-key add -

sudo apt-get update && sudo apt-get install mkvtoolnix mkvtoolnix-gui


---

### Post by twipley on 2012-09-08
Taxi Driver, Apocalypse Now, and Raging Bull amateurs on the quest of tweaking their future *non-DNRed* release possessions:

```
# run the following line from the terminal (ctrl-alt-t): sudo gedit /etc/apt/sources.list
# then, append the two following lines to the end of the therefore-opened sources-list file:

deb http://www.bunkus.org/ubuntu/precise/ ./
deb-src http://www.bunkus.org/ubuntu/precise/ ./

# then, open this file this time not using the "display," but the "run in terminal" button;
# take care, though, to input account password moments after having opened this file that way;

wget -O - http://www.bunkus.org/gpg-pub-moritzbunkus.txt | sudo apt-key add -

sudo apt-get update && sudo apt-get install mkvtoolnix mkvtoolnix-gui

```

source: [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

[http://www.dvdbeaver.com/film/dvdreviews18/taxi_driver_dvd_review.htm](http://www.dvdbeaver.com/film/dvdreviews18/taxi_driver_dvd_review.htm)
[http://www.dvdbeaver.com/film/DVDCompare8/ragingbull.htm](http://www.dvdbeaver.com/film/DVDCompare8/ragingbull.htm)
[http://www.dvdbeaver.com/film/DVDCompare3/apocalypsenow3.htm](http://www.dvdbeaver.com/film/DVDCompare3/apocalypsenow3.htm)

---

