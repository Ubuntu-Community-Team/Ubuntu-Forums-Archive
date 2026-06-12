---
title: "Kubuntu newbie: how do I install MP3 support?"
date: 2006-02-22
forum: General Help
---

### Post by Qwertie on 2006-02-22
I have the impression I should use "Adept" for all my installation needs (I see no Synapse.) I saw some instructions for adding "universe" and "multiverse" to Synapse on another page but I don't know how to map that knowledge to Adept. 

Under "Manage Repositories" I see four lines labelled "universe" but no "multiverse". The instructions I saw said to install gstreamer0.8-mad. There are many gstreamer0.8 packages but "mad" is not listed. Where is it and what makes it so mad? 

On an unrelated note, I need to install Java 5 JRE. Should I 
1. Try to do it with Adept
2. Download the "Linux RPM" from [http://java.com:80/en/download/manual.jsp](http://java.com:80/en/download/manual.jsp) 
3. Download the "Linux" version from the same place?

---

### Post by Qwertie on 2006-02-22
I found my solution here:

[http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10)

I needed to right-click on the "universe" repositories and click Enable (I wondered why those lines were displayed in gray!)  Then I could install gstreamer0.8-mad and amaroK could play MP3s after I restarted it.

Still puzzled about Java tho.

---

### Post by nickle on 2006-02-22
Use Automatix to install all this stuff:

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

