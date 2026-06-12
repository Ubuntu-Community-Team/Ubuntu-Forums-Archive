---
title: "How do I convert avi files to mpg?"
date: 2006-05-26
forum: General Help
---

### Post by chris_andrew on 2006-05-26
Hi,

I have an avi file that I would like to play on my tv/dvd player. Unfortunately my DVD player doesn't support avi. It does support mpg, though. Can I convert one to the other? If so, how?

I'd prefer to use the standard Ubuntu repositories.

Many thanks,

Chris.

---

### Post by Denis on 2006-05-26
It think this can be done with ffmpeg. That's a simple command line program, available in the universe repository. Look in the manual or on the internet for detailed information about how to use it.

---

### Post by chris_andrew on 2006-05-26
Cool, will check it out, and let you know.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-05-26
Hmmmmm,

Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodeccvs51 (>= 3:20060323) but it is not going to be installed
          Depends: libavutilcvs49 (>= 3:20060323) but it is not going to be installed
          Depends: libogg0 (>= 1.1.3) but 1.1.2-1 is to be installed
          Depends: libvorbis0a (>= 1.1.2) but 1.1.0-1ubuntu1 is to be installed
          Depends: libvorbisenc2 (>= 1.1.2) but 1.1.0-1ubuntu1 is to be installed




Any ideas?

Cheers,

Chris.

---

### Post by adamkane on 2006-05-26
Video conversion howto for Ubuntu:
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

---

### Post by chris_andrew on 2006-05-26
Adam,

Thanks for the URL.  It is having problems resolving, but I will keep trying.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-05-26
Thanks for the article.  I just keep getting dependency problems for al of these apps, unlike my standard repositories.  Maybe i'll have to leave it.

Thanks,

Chris.

---

### Post by Denis on 2006-05-26
[QUOTE=chris_andrew]Thanks for the article.  I just keep getting dependency problems for al of these apps, unlike my standard repositories.  Maybe i'll have to leave it.

Thanks,

Chris.[/QUOTE]Too bad it didn't work. Maybe you have to check your sources.list? Those problems with installing ffmpeg and mplayer may indicate some problem.

---

### Post by chris_andrew on 2006-05-26
Denis,

Thanks.  My sources are fine, but as mentioned, I seem to get a dependency problem.  Thanks for everybody's help.

Chris.

---

### Post by blackjack6.21.91 on 2006-05-26
[http://ubuntuforums.org/showthread.php?t=62625&highlight=video+conversion](http://ubuntuforums.org/showthread.php?t=62625&highlight=video+conversion)

i dont think there are any dependencies that aren't installed in default ubuntu

---

### Post by adamkane on 2006-05-27
We're here to help, if you want to share your dependency problems.

The site doesn't always resolve on the first click. I had to put my cursor in the address bar and press enter to make it load.

---

### Post by wouterommeslag on 2006-05-29
I use DeVeDe. It works just fine. The only drawback is that you can't add subtitles from a srt file to the DVD....  You can find all info [here]("http://www.rastersoft.com/programas/devede.html")

---

