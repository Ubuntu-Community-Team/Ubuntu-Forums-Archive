---
title: "vob to avi"
date: 2006-01-24
forum: General Help
---

### Post by da1 on 2006-01-24
yello, i'm still new to this stuff and wonderd about making dvd backups. I ripped a dvd using dvd:rip and formed a vob. Now i'd like to encode it(or whatever the term is) into a smaller file lile .ai and burn it. please help, i'm lost. can't use gnomebaker, or easyTAG i don't think. and i get a tad lost in dvd:rip.
it mentions tanscodes and attempt to do it, a message saying: PSU core only available for ripped dvd's. so i'm confused, please help!

---

### Post by endersshadow on 2006-01-24
To use dvd::rip, you have to either transcode while still in the "project" of ripping, or save the "project" and then open it back up and then transcode.  However, this takes, well, forever.

Note: Please read all the way through this before doing anything concerning ffmpeg :KS

You can try ffmpeg, but you'll have to fix it first, like so:

We'll build it from source...but don't worry, it won't hurt.  We'll also need to install some other libraries.  So, here goes:

```
sudo apt-get build-dep ffmpeg
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev
apt-get source ffmpeg
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
make
sudo checkinstall -D make install
```

It will go through a bunch of stuff and prompt you on the last command for a few things. First, hit y to create docs, then just hit enter at the EOF question. Next, it will take you to the name and version. Edit #2 (name) to be ffmpeg, then edit #3 (version) to be something newer than what it is...so, either 1.cvsxxxxxx or some other way. I had a bit of trouble with this step, so I simply did a sudo make install instead of the whole checkinstall. If you don't mind not having a dpkg for it, then I'd recommend going straight to a sudo make install.

Once that is done, you can go on to using ffmpeg:

```
ffmpeg -i vobfile.vob -f avi -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec mp3 -ab 192 out.avi
```

Alternatively to dvd::rip, you can use vobcopy.  Install it using this command:

```
sudo apt-get install vobcopy
```

Then, to use it, simply do this:

```
vobcopy -l -t name\ to\ call\ ripped\ file -n titlenumber -i /dev/dvd -o /path/to/output/directory/
```

To get infos on titles, use this command:

```
vobcopy -I
```

Alternatively, I've written a program to encode videos for the iPod Video using vobcopy and ffmpeg.  It automatically fixes ffmpeg for you, so you won't have to do the above steps.  It can be found [here](http://ubuntuforums.org/showthread.php?t=114946).  If you install it, and then do:

```
sudo gedit /usr/bin/ipodvidenc
```

On line 136-138 change this:

```
if `ffmpeg -i "${myin}" -f mp4 -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec aac -ab 192 -s 320x240 -aspect 4:3 "${myfile}" &> ${HOME}/.ipodvidenc/log`; then
```

To this:

```
if `ffmpeg -i "${myin}" -f avi -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec mp3 -ab 192 "${myfile}" &> ${HOME}/.ipodvidenc/log`; then
```

And change lines 203-205 from this:

```
if `ffmpeg -i "${infile}" -f mp4 -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec aac -ab 192 -s 320x240 -aspect 4:3 "${outfile}"`; then
```

To this:

```
if `ffmpeg -i "${infile}" -f avi -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec mp3 -ab 192 "${outfile}"`; then
```

---

