---
title: "Changing file permissions for Frets on Fire"
date: 2010-08-02
forum: General Help
---

### Post by harobikes34 on 2010-08-02
Hi i am pretty new to Ubuntu and i just installed frets on fire and downloaded a bunch of songs. The directory is /usr/share/games/fretsonfire/data and when i try to add the song folders i down loaded i get A Error Permission denied error every time i try to add them. I am an administrator account and i just want to play songs. How do i make it possible to add the new song folders?

---

### Post by harobikes34 on 2010-08-02
I searched more until i found this which worked.
sudo chmod 777 -R /usr/share/games/fretsonfire/data/songs/

---

