---
title: "Can't start Eclipse after 12.04 upgrade"
date: 2012-04-27
forum: General Help
---

### Post by JPurdy on 2012-04-27
I just upgraded to 12.04 and I cannot get Eclipse up & running. I did some looking around and have tried nuking eclipse and reinstalling it. I've tried running it w/ the -clean argument and I've nuked my .eclipse and ~/workspace/.metadata directories to see if that fixes it, but I still cannot get the program up & running.

Can someone help point me in the right direction?

This is the error log I'm seeing:

[http://pastebin.com/rCDmSpTx](http://pastebin.com/rCDmSpTx)

Thanks!

---

### Post by cmcginty on 2012-04-30
I had the exact same problem. I ended up remove all of my java packages (except for a few "required" ones), then installing the eclipse package.

This got past that error, but inside of eclipse, all of the editor windows show and error instead of the actual files. 

Right now I'm trying to re-import my project from scratch.

---

### Post by JPurdy on 2012-04-30
There was another post somewhere that said to try 'sudo eclipse' to have some final configuration stuff done, which worked for some people, but that didn't work for me.

I ended up having to uninstall eclipse and just download it from the main site and run it from the unzip'd file.

---

