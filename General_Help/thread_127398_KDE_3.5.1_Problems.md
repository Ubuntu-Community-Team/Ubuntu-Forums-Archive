---
title: "KDE 3.5.1 Problems"
date: 2006-02-08
forum: General Help
---

### Post by sunny_nwho on 2006-02-08
Hi guys...yesterday i removed my whole ubuntu and installed Kubuntu fresh and then updated to KDE 3.5.1 accordig to the instruction on the kubuntu website...but i cannot access wireless now.....and every time i try to enable the wireless device in Kcontrol or network settings it automatically diables and when i try to configure it it crashes and says it is a bug...does any one have a round about for this or am i grounded...please help me......I never had problems like this with Ubuntu.....

---

### Post by sunny_nwho on 2006-02-11
Hi there....i found a solution for it...i actually edited the network interfaces file and it started working......but does anyone know how i can play media on websites thru konqueror.....i am really stuck here.....i want to use konqueror instead of firefox....please reply to this post....

---

### Post by Single on 2006-02-11
Kaffeine should be automatically intergrated with Konqueror.

If you are looking for other players, I recommend Kmplayer.

But I need more info from you to know how to help. Which kind of media (formats etc) do u wan to play thru Konq? And on what sites?

---

### Post by Neo Ex on 2006-02-11
Look at KControl -> KDE Compontents -> File associations -> [file type] -> Embedding, and be sure that there is 'Kaffeine (kaffeine_part)'.
As Single said, I also reccomend KMPlayer (Kaffeine makes Konqueror crashes when closing the tab where there is a media streaming, for example). It's not in the Ubuntu repositories, but you'll fine some deb packages at [http://kmplayer.kde.org](http://kmplayer.kde.org), which will work with Ubuntu (if you prefer you can compile from the source, obviously).

---

