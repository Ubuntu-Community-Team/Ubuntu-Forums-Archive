---
title: "Howto: Successfully Play Matroska With Vlc"
date: 2006-02-09
forum: General Help
---

### Post by terry98 on 2006-02-09
i noticed that many people are complaining about not playing mkv files on ubuntu, including myself.....

so i started to compile VLC and noticed that when it's setting the matroska driver it searches for something else... i was able to play mkv installing the development files of

- libebml

- libmatroska

(the files above are mandatory....)

- libmp4

(nobody has ever said anything about needing this one...)

yeah after i installed the libmp4 development i could compile VLC 0.8.4a with matroska support, to check if your vlc was compiled with mkv support type
"vlc --list |grep mkv" there should appear a line about mkv demuxer.....;)

---

### Post by frodon on 2006-02-09
Could you add step by step explainations and add that in the customisation tips & tricks forum, i'm sure users (especilly beginners) will enjoy that ;)

Thank you anyway for the tip

---

### Post by terry98 on 2006-02-09
ok.. ill do that

---

### Post by frodon on 2006-02-09
Thanks a lot, you rock ;)

---

