---
title: "Firefox cannot locate local network to upload files to websites"
date: 2011-11-30
forum: General Help
---

### Post by thh123 on 2011-11-30
We are switching all our windows machines to the latest ubuntu and things seem to be ok...

We can access the local server (W7) machine via ubuntu just fine

When we go to a (any) websites to upload images, we cannot access our local server to upload the files. Is it a Firefox thing or a Ubuntu thing

As a newbie, I am lost as to why we cannot search the local network to upload files via firefox to websites

---

### Post by maverickaddicted on 2011-11-30
Same here,I also cannot use network folders Firefox, as well as Chrome browsers.

Take a look at here, it will not solve your problem, but will give you general idea about the issue.

[https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/2194](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/2194)

---

### Post by polki@mac.com on 2011-11-30
Would a softlink to .gvfs solve the problem? It works in a java program here.

cd /home/username
ln -s .gvfs namethishowyoulike

To access .gvfs just goto the linked folder called "namethishowyoulike".
I haven't tried uploading files in FF, but it's worth a shot.

---

