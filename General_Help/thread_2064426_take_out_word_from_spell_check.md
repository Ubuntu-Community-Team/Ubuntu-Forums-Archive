---
title: "take out word from spell check"
date: 2012-09-29
forum: General Help
---

### Post by mike555 on 2012-09-29
I'm trying to take the word "prof" from my LibreOffice spell check, I edited the .dic files , but the word still doesn't show as misspelled . I want this because I often misspell the word "proof" as prof and I want the spell check to show it as misspelled.
 perhaps there are more .dic files to edit?

---

### Post by Peter Maunder on 2012-09-29
I don't know how to remove a word from the dictionary. However, I do use AUTOCORRECT to correct my LibreOffice typing errors on the fly. For example I often type TEH rather than THE. When I actually wish to type TEH I just overide the suggested correction.

---

### Post by mike555 on 2012-09-29
Problem is the spell check doesn't give me an option, it doesn't show "prof" as misspelled "proof" , because prof , I guess is a word ..... 
   So if I can take the word prof out of the spell check word list , then I thought it would show prof as misspelled proof.
    Hasn't anyone out there taken words out of the spell check list before ? if so please help me.

---

### Post by rai4shu2 on 2012-09-30
If you have a system setup like mine, then it uses Hunspell for checking. In which case, you can edit the dictionary like this:

```
sudo leafpad /usr/share/hunspell/en_US.dic
```

It appears to be plain text, so you just edit it. I think. I've never tried that, so please be careful.

---

### Post by mike555 on 2012-09-30
rai4shu2  thanks for trying, but I tried that and I also edited the USR/share/dict files , but it still shows   prof as a correct word.
  perhaps there is somewhere else I need to edit?

---

### Post by mike555 on 2012-09-30
even my dictionary shows it as spelled right , so there must be another file I haven"t edited somewhere.
[IMG]http://i45.tinypic.com/2cdycmu.jpg[/IMG]

---

### Post by rai4shu2 on 2012-09-30
Is your dictionary configured to go to localhost (or somewhere on the LAN)?

---

### Post by mike555 on 2012-09-30
I think LibreOffice uses the aspell .dic file on this computer, I thought if I took the word off the list it would think it was misspelled , but perhaps I should have instead put some kind of flag on the word.  
  I even tried making a personal .aspell.en.pws in my /home folder, but that didn't work.

---

### Post by rai4shu2 on 2012-09-30
Maybe you should double-check LibreOffice's settings. Go to Tools / Options / Language Settings / Writing Aids and make sure that only the modules you want to use are selected.

---

### Post by mike555 on 2012-09-30
Ok, I got it, I had to delete the word " prof " from the /usr/share/hunspell/en_US.dic  file  ( not the Aspell .dic ) .
   Now LibreOffice shows prof as misspelled like I wanted.

---

