---
title: "youtube-dl latest version"
date: 2010-04-15
forum: General Help
---

### Post by xbaez on 2010-04-15
Hello
How can I install youtube-dl and keep it up to date?

the latest youtube-dl has much more options than my current one

however, when I do

apt-get install youtube-dl
it says I have the latest versions

is there maybe a repo I'm unaware of?

Another thing, can Youtube ban my IP for using Youtube-dl and install reCaptcha after a while?

One time I programmed a spider to search for youtube videos, and the spider will reproduce the video directly from my website

I guess youtube didn't liked that, and then youtube banned my IP forever, the spider required reCaptcha

thanks a lot

---

### Post by maddg3241 on 2010-04-15
by youtube-dl do you mean a downloader?

---

### Post by xbaez on 2010-04-15
Here are the differences between the latest version of youtube-dl (script is called youtube) and the current version of youtube-dl (script is called youtube-dl)

youtube --help
Usage: youtube [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -U, --update          update this program to latest stable version
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)

  Authentication Options:
    -u UN, --username=UN
                        account username
    -p PW, --password=PW
                        account password
    -n, --netrc         use .netrc authentication data

  Video Format Options:
    -f FMT, --format=FMT
                        video format code
    -b, --best-quality  download the best quality video possible
    -m, --mobile-version
                        alias for -f 17
    -d, --high-def      alias for -f 22
    --all-formats       download all available video formats

  Verbosity / Simulation Options:
    -q, --quiet         activates quiet mode
    -s, --simulate      do not download video
    -g, --get-url       simulate, quiet but print URL
    -e, --get-title     simulate, quiet but print title
    --no-progress       do not print progress bar

  Filesystem Options:
    -t, --title         use title in file name
    -l, --literal       use literal title in file name
    -o TPL, --output=TPL
                        output filename template
    -a F, --batch-file=F
                        file containing URLs to download
    -w, --no-overwrites
                        do not overwrite files
    -c, --continue      resume partially downloaded files
root@server:/usr/local/bin# youtube-dl --help
Usage: youtube-dl [options] video_url

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -u USERNAME, --username=USERNAME
                        account username
  -p PASSWORD, --password=PASSWORD
                        account password
  -o FILE, --output=FILE
                        output video file name
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         print final video URL only
  -2, --title-too       used with -g, print title too
  -f FORMAT, --format=FORMAT
                        append &fmt=FORMAT to the URL
  -b, --best-quality    alias for -f 18

---

### Post by xbaez on 2010-04-15
> **maddg3241 said:**
> by youtube-dl do you mean a downloader?

It's a program to download youtube videos

---

### Post by lisati on 2010-04-15
Thread closed. See [here]("http://ubuntuforums.org/showthread.php?t=1429211")

---

