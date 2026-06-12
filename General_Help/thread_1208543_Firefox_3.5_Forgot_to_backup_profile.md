---
title: "Firefox 3.5 Forgot to backup profile"
date: 2009-07-09
forum: General Help
---

### Post by RizzLinux1388 on 2009-07-09
Hi everybody I'm new to the forums but I've been using Linux for over a year or so. My problem is that I got really excited when I saw there was a new Firefox out so, impatiently I downloaded the tarball from Mozilla's site and I untarred it and then ran it, but I forgot to backup my profile and I can't seem to get my bookmarks back. I'm pretty sure the bookmarks.html file can be located on my computer but as of right now I can't find it. Thanks for the help, and I'm glad to be apart of this community. :)

---

### Post by RizzLinux1388 on 2009-07-09
Ok I fixed the problem I think. It could also be that I installed the ubuntu firefox package, but all I needed to do was choose the default profile and everything was back to normal. Hope this helps somebody else as well.

---

### Post by lovinglinux on 2009-07-09
Depending on how you installed, Firefox 3.5 will use ~/.mozilla/firefox or ~/.mozilla/firefox-3.5 folders to store profiles. Additionally, some installation methods make automatic backups of your profiles into another folder, like  ~/.mozilla.backup.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

I also recommend reading the Backup section of the tutorial.

---

