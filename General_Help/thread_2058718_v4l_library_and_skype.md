---
title: "v4l library and skype"
date: 2012-09-16
forum: General Help
---

### Post by pwabrahams on 2012-09-16
I'm trying to get skype to work under Kubuntu 12.04, and I've again got the problem I solved under earlier Kubuntus.  It all started because on my Asus K60IJ laptop,the image in a video call is upside down (damn Asus and its hardware maldesign).  The cure is supposed to be to use the v4l library, and in the past that has worked.  But now it seems that I don't have the right version of that library, and I can't figure out how to retrieve it.

The online advice from v4l is this:
> Starting to Karmic, adding the PPA and its key is as simple as:
   sudo add-apt-repository ppa:libv4l
But here's what happens when I try it:
```
pwa@pwa-K60IJ:~/Dropbox/Downloads/Kubuntu$ sudo add-apt-repository ppa:libv4l
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (6, "Couldn't resolve host 'launchpad.net'")
pwa@pwa-K60IJ:~/Dropbox/Downloads/Kubuntu$ skype
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```
Just to clarify, I've set **/usr/local/bin/skype** to this:
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

```
Since that comes first in the path search, the simple command **skype** should work -- and in the past, it did.

---

