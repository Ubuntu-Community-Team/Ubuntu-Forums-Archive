---
title: "Cryptkeeper"
date: 2009-12-21
forum: General Help
---

### Post by benefactor on 2009-12-21
Hi Everyone,

I had recently installed crypt-keeper and today I had cleaned up my external drive. I also used Revelation to store all my other passwords, now by moving all my files to clean up my external disk i had accidentally the folder off revelation in my secure folder, as result that I no longer get to my passwords. Is there a possibility to restore the password from crypt keeper? is there some way to crack it or something? I would not like to lose everything. It's more than 10 years work on it.

Thnx

---

### Post by bodhi.zazen on 2009-12-21
I think you will have more success using a tool such as testdisk or pohotorec to recover the deleted file.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Otherwise, the downside of encryption is if you loose the password, you are SOL.

---

### Post by benefactor on 2009-12-21
the file is not deleted, it is in the encrypted folder => example: file RevelationPasswords and know Encryptedfolder/RevelationPasswords

has something to do with / home / user / .gconf / apps / crypt keeper / %gconf.xml

i think to to reset it

---

### Post by benefactor on 2009-12-21
<gconf>
&#8722;
<entry name="stashes" mtime="1261431264" type="string">
&#8722;
<stringvalue>
/media/FREECOM/.pr1v4t3_encfs
/media/FREECOM/pr1v4t3
/media/MY_BOOK/.B4xup_encfs
/media/MY_BOOK/B4xup
</stringvalue>
</entry>
&#8722;
<entry name="filemanager" mtime="1261431264" type="string">
<stringvalue>nautilus</stringvalue>
</entry>
<entry name="idletimeout" mtime="1261431264" type="int" value="0">
        </entry>
<entry name="keep_mountpoints" mtime="1261431264" type="bool" value="true">
        </entry>
</gconf>

---

### Post by benefactor on 2009-12-21
decoding the files 
/usr/share/locale/en@boldquot/LC_MESSAGES/cryptkeeper.mo
/usr/share/locale/en@quot/LC_MESSAGES/cryptkeeper.mo
/usr/share/locale/en_GB/LC_MESSAGES/cryptkeeper.mo
/usr/share/locale/fr/LC_MESSAGES/cryptkeeper.mo

hope it works

---

