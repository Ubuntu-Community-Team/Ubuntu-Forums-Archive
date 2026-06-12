---
title: "File system help"
date: 2011-09-27
forum: General Help
---

### Post by surge031 on 2011-09-27
Hi all,

On my system, Ubuntu Lucid, I have several folders for downloads namely, Music, Movies, etc and these folders reside in the Downloads directory.

I tried moving a movie(Honey I shrunk the kids) from the Download directory to the Movie folder  by typing "mv  honey* Movies" Apparently I messed something up because now I cant access the Movie folder. The "Movie" folder had a purple color and now it's white.

How can I fix ths?

---

### Post by pastalavista on 2011-09-27
If you used the syntax you posted here, you replaced the directory "Movies" with the honey* file. Why didn't you just cut and paste in Nautilus? Sorry, but I don't think there is any way to undo it. What do the properties say when you right-click on it? 

BTW the correct syntax would be: mv honey* /Movies/honey*

---

### Post by Basher101 on 2011-09-27
> Why didn't you just cut and paste in Nautilus? wondering the same...why make it easily when it can be done difficult

---

### Post by surge031 on 2011-09-27
> **pastalavista said:**
> If you used the syntax you posted here, you replaced the directory "Movies" with the honey* file. Why didn't you just cut and paste in Nautilus?
Actually my setup is a bit more involved that that. I built a NAS system using unRaid  that in the basement and i use my Ubuntu to access it.

---

### Post by surge031 on 2011-09-27
> **pastalavista said:**
> If you used the syntax you posted here, you replaced the directory "Movies" with the honey* file. Why didn't you just cut and paste in Nautilus?
Actually my setup is a bit more involved that that. I built a NAS system using unRaid  that in the basement and i use my Ubuntu to access it.

---

### Post by surge031 on 2011-09-27
> **pastalavista said:**
> If you used the syntax you posted here, you replaced the directory "Movies" with the honey* file. Why didn't you just cut and paste in Nautilus? Sorry, but I don't think there is any way to undo it. What do the properties say when you right-click on it? 

BTW the correct syntax would be: mv honey* /Movies/honey*

-rw------- 1 root root 78214 Sep 27 05:05 Movies
drwx--x--x 1 root root   176 Sep 26 04:10 Music/

The share drives movies is no longer available

---

