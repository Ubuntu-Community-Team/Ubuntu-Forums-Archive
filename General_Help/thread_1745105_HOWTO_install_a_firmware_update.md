---
title: "HOWTO install a firmware update?"
date: 2011-04-30
forum: General Help
---

### Post by eltonw on 2011-04-30
I am having connection problems with my Ralink card under Natty Narwhal (11.04) on my netbook. Since I bought the machine over 2 years ago, I have never done any hardware updates. Today I came a across a *.bin file to update the firmware on my card.

Would someone kindly provide me some 'newbie' level instructions on how to do this?:confused:

TIA

---

### Post by TeoBigusGeekus on 2011-04-30
If you trust the source of the file, open a terminal, make the file executable
```
chmod +x /path/file.bin
```
and then run it
```
sudo /path/file.bin
```

---

### Post by eltonw on 2011-04-30
> **TeoBigusGeekus said:**
> If you trust the source of the file, open a terminal, make the file executable
```
chmod +x /path/file.bin
```
and then run it
```
sudo /path/file.bin
```

The file is in {myhome] rt2860.bin
ls command confirms that I am in the directory, and I see the file
        sudo +x rt2860.bin  
/entered root password
changes the permissions to executable. BUT
when I do
      rt2860.bin 
/still as root, I get "command not found"

What am I still doing wrong?

also, if I do:
       ./rt2860.bin
I get a bash error
bash: ./rt2860.bin: cannot execute binary file. 
I KNOW that I have changed permissions, since the filename changes colour in the console, and
I can also confirm via 'properties' in nautilus.

---

### Post by TeoBigusGeekus on 2011-05-01
If you did the chmod as root, then I think only root can execute the file.
Try with
```
sudo ./rt2860.bin
```

---

### Post by eltonw on 2011-05-01
> **TeoBigusGeekus said:**
> If you did the chmod as root, then I think only root can execute the file.
Try with
```
sudo ./rt2860.bin
```
sudo ./rt2860.bin
        returns this error message -
./rt2860.bin: 1: Syntax error: word unexpected (expecting ")")

 BTW, elsewhere someone suggested that I **copy** the file to /lib/firmware, but of course this does not write the firmware update to the card BIOS ... which IMVHO, would be the expected thing, *n'est pas*?

The recommendation to rename the old driver and copy is in this thread:
[http://ubuntuforums.org/showthread.php?p=10747902#post10747902]("http://ubuntuforums.org/showthread.php?p=10747902#post10747902")

---

