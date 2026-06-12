---
title: "Utube"
date: 2010-02-04
forum: General Help
---

### Post by noelc on 2010-02-04
Can anyone tell me why Utube videos wont start for me? I,m running firefox on 9.1.

It was working fine. The page loads OK but no movie?

---

### Post by s.fox on 2010-02-04
Hello,

I would try some of the suggestions mentioned [here]("http://ubuntuforums.org/showthread.php?t=1303375").

-Silver Fox

---

### Post by lovinglinux on 2010-02-04
See [this](http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2).

---

### Post by rocket16 on 2010-02-04
I think you do not have a Flash Pugin enabled. If so, you can install it individually, or can install "Ubuntu Restricted Areas" System, to do it. In addition, for downloading those Videos, use youtube-dl.

---

### Post by noelc on 2010-02-04
> **rocket16 said:**
> I think you do not have a Flash Pugin enabled. If so, you can install it individually, or can install "Ubuntu Restricted Areas" System, to do it. In addition, for downloading those Videos, use youtube-dl.

Thanks I do have Ubuntu restricted areas installed but i notice adobe flah is not installed. I get wrong architecture message when i try to install it. this is weird as i had no problem with vidoes before.

I,m not confident using the terminal either

---

### Post by rocket16 on 2010-02-04
Then, go to Adode Flash site, and download the Istaller (Deb). They'll probably automatically detect your Architecture and you'll have no problem. The PAckage is only about 1.8 MB. An alternative Slution is to download the Videos using youtube-dl. To install it, type "sudo apt-get install youtube-dl" in the Console. It is a very small package, even less than 1 MB. Then, in the console, type "youtube-dl address" where address is the url of the Page with your desired video. It will download it with greater speed tha the Browser (since it won't download other advertisements, other links etc.). Then, use Totem or GNOME-Player to play it. And, for viewing it again, you won't have to download it again. Hence this daves time, reduces downloads and further, enabled you to view Videos offline.

---

### Post by rocket16 on 2010-02-04
Oh Sorry, youtube-dl is less than 100 KB.

---

### Post by rocket16 on 2010-02-04
Sometimes Gnash SWF Player also conflicts with Flash-Plugin. D you have Gnash Player installed?

---

