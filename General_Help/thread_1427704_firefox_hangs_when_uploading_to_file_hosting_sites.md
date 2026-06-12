---
title: "firefox hangs when uploading to file hosting sites"
date: 2010-03-11
forum: General Help
---

### Post by ceann817 on 2010-03-11
Hi There.

I am not sure where to put this but please help me anyway.

I am using ubuntu karmic koala and i have firefox web browser. 
Whenever I try to upload files in some file hosting sites, my firefox web browser hangs.
I think the file hosting site is using some kind of uploader that requires java/javascript.

Please help me.
Thanks in advance.

Cecille

---

### Post by mister_playboy on 2010-03-13
What site are you using?  If it's Megaupload, you can try [[COLOR="Orange"]this script[/COLOR]](http://www.expertcore.org/viewtopic.php?f=20&t=1141).  The file will actually upload if you just let it run, but losing use of Firefox for the duration of the upload is very annoying.

---

### Post by kvarley on 2010-03-13
I have this problem for Megaupload and Mediafire, Firefox greys out and you lost all functionality of the browser until the upload is complete. (Unless you force quit the browser and re-open it.)

---

### Post by Uncle Spellbinder on 2010-03-13
I have tie problem with MediaFire. Can't find the link any longer, but I saw somewhere that MediFire does not support linux.

---

### Post by kvarley on 2010-03-14
I have found a solution which appears to work for mediafire (fingers crossed!)

Hit Alt + F2 and in the run box type:
> metacity --replace

Now upload your file and then I imagine you will wish to default back to compiz:
> compiz --replace

It's a minimal change and worth it indeed to be able to upload.

Hope this helps, please let me know how you find it.

---

