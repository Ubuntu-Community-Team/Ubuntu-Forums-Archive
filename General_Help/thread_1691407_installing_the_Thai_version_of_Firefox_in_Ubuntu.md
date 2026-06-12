---
title: "installing the Thai version of Firefox in Ubuntu"
date: 2011-02-19
forum: General Help
---

### Post by Johnnz on 2011-02-19
Hello all,
  Have installed Ubuntu 10.0 (I think it is latest version) and want to install the Thai language version of Firefox from Mozilla website. They have a Linux version download link, but when I click and save it, it is a tar.bz2 file that I can extract but then haven't got a clue how to use the resulting folder named "Firefox" to replace the existing English version on Ubuntu. I cant find an Install file and the only readme file is about the help page on Mozilla website. Neither can I find a .run file anywhere. 

 Please help. 

Thankyou.

---

### Post by I&#9829;HTML5 on 2011-02-20
From [http://support.mozilla.com/en-US/kb/Installing%20Firefox%20on%20Linux](http://support.mozilla.com/en-US/kb/Installing%20Firefox%20on%20Linux):
> [LIST=1]
[*]Download Firefox from the Firefox download page to your home directory.
[*]Open a Terminal and go to your home directory: ```
cd ~
```
[*]Extract the contents of the downloaded file:```
tar xjf firefox-*.tar.bz2
```
[*]Close Firefox if it's open.
[*]To start Firefox, run the firefox script in the firefox folder.
```
~/firefox/firefox
```
[/LIST]

Firefox should now start. You can then create an icon on your desktop to run this command.

---

