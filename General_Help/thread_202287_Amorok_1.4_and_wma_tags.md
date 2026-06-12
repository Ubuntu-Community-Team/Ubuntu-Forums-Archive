---
title: "Amorok 1.4 and wma tags"
date: 2006-06-23
forum: General Help
---

### Post by aum11 on 2006-06-23
Have installed Amarok 1.4 and found it to be incredible.(also had to install ruby to enable lyrics to be accessed).  It is such a good player.

My only problem now is that Amarok will not allow editing of wma song tags.  Obviously I have fairly recently migrated from the dark side.

Any suggestions please?

---

### Post by Castar on 2006-06-23
Unfortunately, the tagging library that Amarok uses (taglib) doesn't support the editing of wma files yet. Have a look [here]("http://blogs.linux.ie/fuzzbucket/2006/01/26/wma-m4a-and-amarok/"). But, given the development speed I'm sure it's coming! ;) Don't forget that the previous version of Amarok 1.3.x didn't even recognise wma files!

---

### Post by aum11 on 2006-06-23
Thanks Castar.  

I guess I will just have to be patient.

---

### Post by Ramses de Norre on 2006-06-23
1.3.x did recognize wma here, but less good then the newer version.
I convert every wma I find to mp3 or ogg ;)

---

### Post by aum11 on 2006-06-23
Thanks Ramses de Norre.

What do You convert with?

Doesn't the quality of the recordings deteriorate even further with another conversion?

---

### Post by Ramses de Norre on 2006-06-23
I use the audio-convert script (in the repos), and I haven't noticed any quality decrease yet.. Maybe there is a little bit but I don't hear it ;)

---

### Post by Foxcow on 2006-06-23
I have a few mp3's that I want to play.  They are on my NTFS storage drive.  I can access and move them to my linux partition but I cant get them to play in Amorok.  Any suggestions?

---

### Post by Castar on 2006-06-24
Can you play them with other players like Kaffeine or Totem?

If you cannot play the files with either player, can you play them when they are located at the NTFS partition?

Because if you cannot play them regardless of where they are, then you don't have mp3 support yet. Have a look [here]("https://help.ubuntu.com/community/RestrictedFormats"). 

I hope this helps :)

---

