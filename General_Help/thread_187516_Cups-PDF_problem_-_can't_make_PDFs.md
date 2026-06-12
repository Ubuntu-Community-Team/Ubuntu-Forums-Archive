---
title: "Cups-PDF problem - can't make PDFs"
date: 2006-06-03
forum: General Help
---

### Post by Muffe on 2006-06-03
Yesterday I installed Cups-PDF from atp-get, and tried to set up a PDF printer, but with no luck. I can't add the printer, and if I edit the printers.conf manually it still doesn't work (copy'n paste from a working configuration on another computer).

Does anyone have experience in getting Cups-PDF to work on Dapper? I have also tried to install and compile the nevest (2.4.0) version from source, and the result is the same.

Thanks.

---

### Post by Hellaxe on 2006-06-03
Same problem here. That´s a must have in my systems.
Please HELP US:mrgreen:

---

### Post by newen on 2006-06-03
from [http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/)
> 
CUPS-PDF requires root privileges since it has to modify file ownerships. In recent distributions the "RunAsUser" option in cupsd.conf is set to "Yes" which removes these privileges. Please make sure to set "RunAsUser No" if you want to use CUPS-PDF.
*** Starting with version 1.2.0 CUPS implements the "RunAsOption" no longer. In order to ensure CUPS-PDF is running with the required root privileges you have to make 'root' the owner of the cups-pdf backend and set the file permissions of the backend to 0700 (root only

---

### Post by yopnono on 2006-06-03
Well the only way I could make the pdf printer to work was to set the permission to "1604755" by setting "set user id"

---

### Post by desperado666 on 2006-06-03
Your Problem ist described here 
[http://ubuntuforums.org/showthread.php?t=81999](http://ubuntuforums.org/showthread.php?t=81999)
and here in german language
[http://wiki.ubuntuusers.de/Druckwerkzeuge](http://wiki.ubuntuusers.de/Druckwerkzeuge)

---

### Post by SkeRoy on 2006-06-04
"RunAsUser" doesn't appear in the new cupsd.conf file of Ubuntu 6.06...

Then... what the solution? Adding it?

---

### Post by Muffe on 2006-06-04
I have noticed the same. I have added it, but it didn't help at all. I have tried all the tips in this thread, but with no luck.

Perhaps anyone width Dapper and Cups-PDF up&go could post a few tips?

---

### Post by yopnono on 2006-06-04
[QUOTE=Muffe]I have noticed the same. I have added it, but it didn't help at all. I have tried all the tips in this thread, but with no luck.

Perhaps anyone width Dapper and Cups-PDF up&go could post a few tips?[/QUOTE]

Ok since people dont read and learn from the posts. I will explain..
1, go to /usr/lib/cups/backend
2, change the permission to 1204755 on the file "cups-pdf" this is done by check the checkbox "Set user ID"

Now you will be able to find the pdf printer in the add printer dialog

---

### Post by shuttleworthwannabe on 2006-06-04
I hate to labor this point here: I am having the same problem. I have installed cups-pdf but the pdf printer is not listed under the add printer options in KDE (kubuntu).

Yopnono, with due respect, I am completely lost with your instructions
1. I went to /usr/lib/cups/backend and there is a file called cups-pdf (it is an executable, so does no topen at all when clicked and kwrite opens it in garbled texts.
2. So this step can not be completed.

The other links on this post do not help either: they all point to other topics.
Help will be much appreciated.

Thanks
1

---

### Post by yopnono on 2006-06-04
[QUOTE=shuttleworthwannabe]I hate to labor this point here: I am having the same problem. I have installed cups-pdf but the pdf printer is not listed under the add printer options in KDE (kubuntu).

Yopnono, with due respect, I am completely lost with your instructions
1. I went to /usr/lib/cups/backend and there is a file called cups-pdf (it is an executable, so does no topen at all when clicked and kwrite opens it in garbled texts.
2. So this step can not be completed.

The other links on this post do not help either: they all point to other topics.
Help will be much appreciated.

Thanks
1[/QUOTE]


Ok sorry. you need to r-click on the file and select properties then select tab permissions.

Also you need to do this as sudo/root.

other way is open terminal
sudo chmod 4755 /usr/lib/cups/backend/cups-pdf

---

### Post by Horizon on 2006-06-04
[QUOTE=shuttleworthwannabe]I hate to labor this point here: I am having the same problem. I have installed cups-pdf but the pdf printer is not listed under the add printer options in KDE (kubuntu).

Yopnono, with due respect, I am completely lost with your instructions
1. I went to /usr/lib/cups/backend and there is a file called cups-pdf (it is an executable, so does no topen at all when clicked and kwrite opens it in garbled texts.
2. So this step can not be completed.

The other links on this post do not help either: they all point to other topics.
Help will be much appreciated.

Thanks
1[/QUOTE]
What's wrong? it seems to work perfectly here. 

1. Install it via apt
2. Go to /usr/lib/cups/backend as root 
3. Right click on the cups-pdf executable, go to permissions and put a tick in "Set User ID"
4. Go to printers and the pdf printer should show up under local printers...
5. When it asks for a manufacturer chose generic and set the model as "postscript color printer (rev3a)"

That's it...just give it a decent name and you're done. Your pdfs should show up in ~/PDF 

**yopnono**, your instructions were spot on, thanks. I forgot I had installed cups-pdf, at least I have it set up now for when I need it :D

---

### Post by LoKi128 on 2006-06-04
I posted a HOWTO, which is still waiting for moderation. The sticking point is the fact that you need to be root to edit the permissions. I did this by opening a terminal and running 'sudo nautilus' and of course, there are other ways.

Thanks all!

---

### Post by sbassett on 2006-06-05
Much kudos to Horizon for the short and sweet guide.

---

