---
title: "Command-line screenshots without heavy programs"
date: 2011-10-01
forum: General Help
---

### Post by J V on 2011-10-01
I'm trying to get ffmpeg to take a screenshot via x11grab for openbox without installing unnecessary junk like imagemagick.

So far I have this:```
ffmpeg -f x11grab -r 1 -s `xrandr | grep \* | cut -d ' ' -f 4` -vframes 4 -i :0.0 -y -f image2 out.png
```

The output file is transparent (Or white I didn't check) - upping vframes to something higher gives an error that the input stream is corrupted.

Incidentally, this is not a very fast way of doing things as ffmpeg takes a while to start up, if there are any lightweight *simple* programs (Probably starting with the letter x ;) ) that can take a screen-capture, that would be great. (And offering a dialogue as to what to do with it would be even better)

---

### Post by TeoBigusGeekus on 2011-10-01
Have a look at scrot.

---

### Post by sisco311 on 2011-10-01
EDIT: TeoBigusGeekus beat me to it.

I'm using scrot.

---

### Post by TeoBigusGeekus on 2011-10-01
> **sisco311 said:**
> EDIT: TeoBigusGeekus beat me to it.

I'm using scrot.

To be recorded in ubuntuforums annals: I've finally beaten sisco in something.

---

### Post by J V on 2011-10-01
I read something bad about it being out of date or something but it does seem to be the best option, thanks :)

---

### Post by sisco311 on 2011-10-01
> **TeoBigusGeekus said:**
> To be recorded in ubuntuforums annals: I've finally beaten sisco in something.

lol

> **J V said:**
> I read something bad about it being out of date or something but it does seem to be the best option, thanks :)

Where did you read it? Did they mention an alternative?

Just try it. If it works for you then good, if not try something else. 

Hmmm, I just checked it out. The latest version was released in 2003 :shock:

But still, I wouldn't say it's out of date. Is the wheel (4th millennium BCE) out of date?

---

### Post by Bonster on 2011-10-02
This what I use for commandline screenshots with alias/function in the ~/.bashrc file

for specific window
#type 'screenshot.win' pick a window with your cursor to take the pix

> screenshot.win() { import -frame -strip -quality 75 "$HOME/screenshot.win_`date +'%F_%Hh%M'`.png" ;}

for full screen
#type 'screenshot' otherwise u can use extra options 
#Usage: screenshot [seconds] [quality]

> screenshot() {
    if ! which scrot &>/dev/null; then
        echo "${FUNCNAME[0]}(): You must first install 'scrot'."
        return 1
    fi

    local delay=1
    local quality=95

    [ "$1" ] && delay="$1"
    [ "$2" ] && quality="$2"

    scrot -q $quality -d $delay "$HOME/screenshot_`date +'%F_%Hh%M'`.png"
}

---

### Post by FakeOutdoorsman on 2011-10-03
> **J V said:**
> I'm trying to get ffmpeg to take a screenshot via x11grab for openbox without installing unnecessary junk like imagemagick.

So far I have this:```
ffmpeg -f x11grab -r 1 -s `xrandr | grep \* | cut -d ' ' -f 4` -vframes 4 -i :0.0 -y -f image2 out.png
```

The output file is transparent (Or white I didn't check) - upping vframes to something higher gives an error that the input stream is corrupted.

As for FFmpeg, the image appears to be mostly/all transparent, but the data is still there. Open the image in GIMP and then choose *Colors > Components > Decompose > OK*. A new gray image will appear. Then choose *Colors > Components > Compose > OK* and a normal looking image will show up.

An easier workaround is adding **-pix_fmt rgb24** to your FFmpeg command:
```
ffmpeg -f x11grab -r 1 -s $(xrandr | grep \* | cut -d ' ' -f 4) -i :0.0 -vframes 1 -pix_fmt rgb24 -y out.png
```

I filed a bug report about this upstream five months ago, but it may not matter now that Ubuntu has moved from FFmpeg to libav due to the personal preference of the maintainer. However, libav cherry-picks commits from FFmpeg on occasion so maybe we will see this fixed someday.

...or just use **scrot**. It does one thing and it does it well.

---

