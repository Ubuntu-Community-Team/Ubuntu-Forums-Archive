---
title: "Mobile Media Converter fails"
date: 2010-11-07
forum: General Help
---

### Post by daldude on 2010-11-07
I had to upgrade to Ubuntu 10.04 64-bit LTS because 9.04 support ended and I installed Mobile Media Converter 1.7.0 and now any time I try to convert any file either video to audio or audio to a different audio file type it fails with the error message below in red and on the support page for MMC someone posted this message I have no idea what they are talking about and how I would do what they did to solve the problem

[FONT=MS Sans Serif, Arial, Helvetica][SIZE=2]I had the same problem on Ubuntu 10.10 64 bits, and I solved it, by seeking the ffmpeg binary on "/". I found two binaries, one who weights 6 Mio and one who weights 95,6 Kio.  I copied the last on /opt/MIKSOFT/MobileMediaConverter/lib/ , replacing the old one, and it works now.
[/SIZE][/FONT]

Error message from Mobile Media Converter below in red :mad:

[COLOR=Red][B]>> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg" -y -vn -i "/media/NTFS_DATA/Movies/Aerosmith-_Janie's_Got_A_Gun.mpg" -acodec libmp3lame -ac 2 -ar 44100 -ab 192k -f mp3 -map_meta_data "/media/NTFS_DATA/Movies/Aerosmith-_Janie's_Got_A_Gun.mp3":"/media/NTFS_DATA/Movies/Aerosmith-_Janie's_Got_A_Gun.mpg" "/media/NTFS_DATA/Movies/Aerosmith-_Janie's_Got_A_Gun.mp3"

>> Result: 
/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg: error while loading shared libraries: libfaac.so.0: cannot open shared object file: No such file or directory
----------------------------

[/B][/COLOR]

---

### Post by daldude on 2010-11-08
I fixed it. I downloaded the 1.6.0 deb package and extracted all the [COLOR=Red]** libfaac**[/COLOR] files into the directory the program was installed in and now it works.

---

### Post by lacroixflo on 2010-11-30
Hi there, I read your posts, but as I am an absolute beginner in ubuntu, I can not find the [FONT=MS Sans Serif, Arial, Helvetica][SIZE=2]ffmpeg binary on "/".
Anyone could help?

Thanks, in advance.:P


[/SIZE][/FONT]

---

