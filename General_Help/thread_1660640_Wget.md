---
title: "Wget"
date: 2011-01-05
forum: General Help
---

### Post by mkr10001 on 2011-01-05
Hi I want to download all the jpg files on a website but i foudn this on the internet but it doesn't work it only gets the index file.
(changed foobar to my website)

wget -r -l4 --no-parent -A.jpg [http://foo.bar.com](http://foo.bar.com)

and 

wget -r -A.jpg [http://foo.bar.com](http://foo.bar.com)


i just want to have a mess about with it really but i can't make it work


anyone help?

---

### Post by JeffDavidoff on 2011-01-06
The parameter -A requires a comma-separated lists of file name suffixes or patterns to accept.

```
wget -r -A jpg,jpeg  www.example.com
```You seem to have a . (dot) between the A and jpg. Did you try to remove the dot?

---

### Post by mkr10001 on 2011-01-11
> 
C:\Users\Michael>wget -r -A jpg,jpeg [www.xxx.co.uk](www.xxx.co.uk)
SYSTEM_WGETRC = c:/progra~1/wget/etc/wgetrc
syswgetrc = C:\Program Files\GnuWin32/etc/wgetrc
--2011-01-11 17:39:17--  [http://www.xxx.co.uk/](http://www.xxx.co.uk/)
Resolving [www.xxx.co.uk](www.xxx.co.uk)... xx.xx.xx.xx
Connecting to [www.xxx.co.uk|xxx.xx.xxx.xx|:80](www.xxx.co.uk|xxx.xx.xxx.xx|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1144 (1.1K) [text/html]
Saving to: `[www.xxx.co.uk/index.html](www.xxx.co.uk/index.html)'

100%[======================================>] 1,144       --.-K/s   in 0s

2011-01-11 17:39:18 (29.9 MB/s) - `[www.xxx.co.uk/index.html](www.xxx.co.uk/index.html)' saved [
1144/1144]

Removing [www.xxx.co.uk/index.html](www.xxx.co.uk/index.html) since it should be rejected.

FINISHED --2011-01-11 17:39:18--
Downloaded: 1 files, 1.1K in 0s (29.9 MB/s)

C:\Users\Michael>



This is what happens

(Obviously not xxx.co.uk though lol)

---

### Post by gmargo on 2011-01-11
Does the site have a robots.txt file? ([Wikipedia link]("http://en.wikipedia.org/wiki/Robots.txt")) **wget** respects it if present.  

Also, if all the links on the page are generated through javascript, then wget has no way of knowing what they are.

---

### Post by mkr10001 on 2011-01-12
nope. no robots.txt

the links are just normal links.

---

### Post by soad6 on 2011-01-24
I have a similar proposal to what this guy posted which would be how can I use wget to get a file like a torrent or is it possible? I want it to run thru the command line and not transmission. Also, if this can't be done how can I download a file, mp3, image or anything using wget? I know that I used it before in a bash script to get a deb file constantly, but not exactly sure how it works. Also will wget get the file even though the page is blocked by a windows server or will I need to get permission from the server or remove the firewall program that blocks the site? Thank you.

---

