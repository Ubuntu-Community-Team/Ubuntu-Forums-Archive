---
title: "Fonts in firefox really weird :("
date: 2006-06-06
forum: General Help
---

### Post by Poka64 on 2006-06-06
I'm using firefox from mozilla, and the fonts are really weird compared to the ones with the firefox build that ubuntu dapper has. 
With the build from mozilla I have to increase the textsize to read it correctly, especially "=" and some other characters are really screwed up :(

Is there a way to fix this ?

---

### Post by bruce89 on 2006-06-06
Why are you using the Mozilla build of firefox?  Firefox 1.5.0.4 will be built for Ubuntu soon, anyway it's not as if you can hijack Linux.

---

### Post by Poka64 on 2006-06-06
Well, is there a way to revert?
Used some script that I found here, forgot to bookmark it :)

---

### Post by Poka64 on 2006-06-06
Found the script I used:

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

---

### Post by bruce89 on 2006-06-06
I'm sure that Aysiu will help, but that might be later.

---

### Post by Poka64 on 2006-06-06
Well, I know how to start ubuntus build of firefox:

```
/usr/bin/firefox.ubuntu
```

But I don't know how to remove the mozilla build :(

---

### Post by Ramses de Norre on 2006-06-06
It looks like it's installed to /opt/firefox, there will be a directory *.default (* can be anything, kind of a username) copy from that following files to ~/.mozilla/firefox/*.default (can be another username for *) ```
bookmarks.html cert8.db cookies.txt formhistory.dat hostperm.1 key3.db signons.txt history.dat  mimeTypes.rdf
```
Then do  ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```
If everything works you can delete the previous firefox ```
 sudo rm -r /opt/firefox
```

---

### Post by Poka64 on 2006-06-06
Ramses de Norre: Worked perfectly, thx for the help! :)

---

