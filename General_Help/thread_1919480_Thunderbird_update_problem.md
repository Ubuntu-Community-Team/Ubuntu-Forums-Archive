---
title: "Thunderbird update problem"
date: 2012-02-02
forum: General Help
---

### Post by KarenAK on 2012-02-02
Thunderbird just notified me that I am using version 3.1 and that it won't be supported any longer.

This came as a bit of a surprise to me because I thought that Thunderbird would be updated regularly like all the other programs and that I was using the latest version ?

Ok, so I followed the link and downloaded the Linux version (10)

But now I don't know what to do with the tar.bz2 file. Usually I double-click it and it will install ? 
Not so. Just lets me extract it, select a folder and that's it.

Now, how do I update this old Thunderbird thing ? I really do NOT want a new installation where I have to redo all the config, add accounts and such. And I most certainly don't want to lose my calendar !

Any help is much appreciated !

Thanks in advance :-)

karen

---

### Post by hwttdz on 2012-02-03
Get a terminal and go to the directory containing the .tar.bz2 file.

then extract the archive to /usr/local/lib
```
sudo tar -xf thunderbird-10.0.tar.bz2 -C /usr/local/lib/
```

then setup the link (don't know why thunderbird works like this...)
```
sudo ln -s /usr/local/lib/thunderbird/thunderbird /usr/local/bin/thunderbird
```

Then so long as your path contains /usr/local/bin before /usr/bin you should be good to go.  Try typing just "thunderbird" on the line and hitting enter.  I got some warnings running it, but nothing I'm overly worried about.  And it picked up all my accounts fine and even went to check for new versions of my addons.  

Also, happy 1000 to me.

---

### Post by sikander3786 on 2012-02-03
Why install from the .tar.bz2 packages when a stable PPA is available and would keep you updated with the newer version via the Update Manager?

For instructions, please refer to the Natty section here (as I guess you are using Natty as mentioned in your signature):

[http://www.tuxgarage.com/2011/12/thunderbird-9-available-in-stable-ppa.html](http://www.tuxgarage.com/2011/12/thunderbird-9-available-in-stable-ppa.html)

---

### Post by KarenAK on 2012-02-03
!!!!
This worked like a charm !

Thank you :-)

It never occurred to me that I didn't have the thunderbird repository... or that I had to have it specially installed *sigh

Lesson learned.

Thanks !

---

### Post by KarenAK on 2012-02-03
[@hwttdz]("http://ubuntuforums.org/member.php?u=175488")

Thank you for your reply !

Guess I must read up on those tar things....

---

