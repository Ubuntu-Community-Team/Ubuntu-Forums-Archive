---
title: "&quot; Add to vlc playlist &quot; option in menu"
date: 2011-07-05
forum: General Help
---

### Post by raja.genupula on 2011-07-05
Hey guys in windows i think i have  a option like as add to vlc media player play list but after moving to linux , i dont have that option . i have tried some nautilus scripts from gnome site but they didnt work to me . 


                need help to solve this . thanks in advance ,

---

### Post by Vaphell on 2011-07-05
configure vlc to run in single instance mode

install nautilus-actions
```
sudo apt-get install nautilus-actions
```

run it
```
nautilus-actions-config-tool
```

create an entry
- name it as you wish (Context label)
- configure command part
path: vlc
parameters: --playlist-enqueue %M
- fine-tune selection options (extension/mimetype, single/multiple selection etc)

reload nautilus
```
nautilus -q
```
done.

if you rightclick on files that are supposed to match the criteria, your custom entry should be there.

---

### Post by raja.genupula on 2011-07-07
thank you man , i will try it .

---

### Post by raja.genupula on 2011-07-08
> **Vaphell said:**
> configure vlc to run in single instance mode

install nautilus-actions
```
sudo apt-get install nautilus-actions
```run it
```
nautilus-actions-config-tool
```create an entry
- name it as you wish (Context label)
- configure command part
path: vlc
parameters: --playlist-enqueue %M
- fine-tune selection options (extension/mimetype, single/multiple selection etc)

reload nautilus
```
nautilus -q
```done.

if you rightclick on files that are supposed to match the criteria, your custom entry should be there.


at the parameters up to which i have to insert , i had inserted upto %M , i got the option add to vlc playlist but when i open mp3 file with that then its opening in new player . but i have solved this by making enable in these two cases one is enabling at single mode and 2nd is (not exactly remembered) enqueue playlist  when vlc open ......by this i can add up songs to current playlist . works fine man .

---

