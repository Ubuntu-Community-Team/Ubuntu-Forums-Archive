---
title: "Python script won't read a web address"
date: 2011-09-15
forum: General Help
---

### Post by searchfgold6789 on 2011-09-15
Hi,
I am having a problem with a python script that I downloaded. The script can be found [here ]("https://github.com/rg3/youtube-dl/raw/2011.09.18/youtube-dl")and it is called youtube-dl. It is also available from the repos, but both versions have the same problem. I have python 2.6 and 2.7 installed, and the script requires ">=2.5".
The script is supposed to take a url from youtube and then get video from it. However it only really understands the physical part of the url [SIZE=1](if you can call it physical)[/SIZE] up to a question mark (?) symbol. For example:```

richie@richie-Dimension-4600i:~/Projects/iPod$ python /home/richie/Projects/Youtube/youtube-dl.py -cit --format=mp3 "http://www.youtube.com/view_play_list?p=PL0A413B52C0060F90&F"
[youtube] Setting language
[youtube] view_play_list: Downloading video webpage
ERROR: unable to download video webpage: HTTP Error 404: Not Found
```
As you can see, python will only see the part of the url up to the question mark, which obviously doesn't exist on the web.
So any help with this would be a great relief to me.
Thank you!
 - search

---

### Post by btindie on 2011-09-15
That youtube URL you've given is a link to a playlist.. I don't know how that program works but I'd have thought you'd need to give it the URL to a video?

I've tried it myself on Ubuntu 10.10 without the formation option and it downloaded a video fine. If you want to convert it to mp3 you may require some additional libraries to be installed.

---

### Post by dniMretsaM on 2011-09-15
I don't know if youtube-dl works with YT playlists. There are some that do. Clive/CClive might have it integrated into them, not sure. Go to their SourceForge pages for more info on that.

---

### Post by searchfgold6789 on 2011-09-16
I am absolutely positive that youtube-dl has the ability to download playlists, as long as they are in the following format: [http://www.youtube.com/view_play_list?p=VIDEO#](http://www.youtube.com/view_play_list?p=VIDEO#), which as you can see from my post they are.
I tried clive and cclive. They have the same sorts of errors as youtube-dl does, except they are pearly instead of pythony.

---

### Post by dniMretsaM on 2011-09-16
> **searchfgold6789 said:**
> I am absolutely positive that youtube-dl has the ability to download playlists, as long as they are in the following format: [http://www.youtube.com/view_play_list?p=VIDEO#](http://www.youtube.com/view_play_list?p=VIDEO#), which as you can see from my post they are.
I tried clive and cclive. They have the same sorts of errors as youtube-dl does, except they are pearly instead of pythony.
Hmm... That's odd. Have you tried a different playlist? And maybe you could use [this](http://code.google.com/p/umph/) and use the displayed URL's and download the vids individually (or via a text file if youtube-dl supports that, Clive/CClive do if it doesn't). And CClive's errors probably aren't  "perly" since it's written in C...

---

### Post by searchfgold6789 on 2011-09-16
No, youube-dl won't download any other playlist :(
I will keep your other suggestion in mind, but I would first like to know if there is an easier solution before I install all all of those dependencies for the perl scripts.

---

### Post by thebarisaxkid on 2011-09-16
To get a 404 error, probably means the script could not find the page at all. Have you tried downloading any individual videos? Try one right now.

---

### Post by searchfgold6789 on 2011-09-16
SOLVED:
randomly started working after ```
sudo apt-get install youtube-dl
youtube-dl -U
youtube-dl (options) (url)
```

---

### Post by thebarisaxkid on 2011-09-16
Which is why I always prefer using things from the repos :P

---

