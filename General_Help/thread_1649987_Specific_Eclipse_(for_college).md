---
title: "Specific Eclipse (for college)"
date: 2010-12-20
forum: General Help
---

### Post by Trevor3443 on 2010-12-20
My college requires us to use their specific version of Eclipse which can be found at this site: [http://web-cat.cs.vt.edu/eclipse/install.php](http://web-cat.cs.vt.edu/eclipse/install.php) (direct link to package: [http://web-cat.cs.vt.edu/eclipse/distros/vteclipse-350-20090921-linux.tar.gz](http://web-cat.cs.vt.edu/eclipse/distros/vteclipse-350-20090921-linux.tar.gz) )

They provide a *tar.gz* file containing their customizations, but within it it is missing a configurations file that is needed to use the ./configure command when installing from source. (I was following this guide: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) ) [[It does have a configurations *folder*, but it still didn't work]]

When I looked at the extracted contents though, it seems like it has already been compiled, but when I click on the eclipse executable nothing happens visually.

Picture of this file:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179010&stc=1&d=1292903992[/IMG]

I have Googled my way around for three hours on this subject, and finally am throwing in the towel. I am trying to get away from Windows in general, so I'll keep on trying till I get it working.

Thanks.

[edit: I know little to nothing about Linux, but plan to learn more as I use it. Any of the terms used above may be wrong!]
[edit: uploaded a picture]

---

### Post by Nytram on 2010-12-20
Try executing it from the terminal and noting the error message.

---

### Post by Trevor3443 on 2010-12-20
> **Nytram said:**
> Try executing it from the terminal and noting the error message.

to run a something its just ./ then eclipse right?
If so this is what I get: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179016&stc=1&d=1292906274[/IMG]

And if I cant get it working, and is a good eclipse alternative for Java?

---

### Post by djeikyb on 2010-12-21
Yes, running ./eclipse is how you start it. You might try "strace ./eclipse". Post the output here as a file, or at least the last several lines.

---

### Post by Nytram on 2010-12-21
That's strange, it not giving an error message. I'm not sure what the problem is.

A good alternative IDE for Java is Netbeans, which can be easily installed via the Software Centre.

---

