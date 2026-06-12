---
title: "Installing OpenOffice in Ubuntu 10.04 LTS"
date: 2011-10-05
forum: General Help
---

### Post by Macrotus on 2011-10-05
Hi all

I unistalled the OpenOffice.org software and now I have troubles with installing it again. I tried to install LibreOffice alongside with OpenOffice but it didn't work. So I uninstalled OpenOffice just to see LibreOffice in action.

Now I want to reinstall OpenOffice. How can I do that? I've tried everything I've found on the Internet. Nothing works (or then I just don't know how).

---

### Post by ajgreeny on 2011-10-05
What is wrong with Libreoffice and how did you install it?   Similarly, how are you attempting to install openoffice?

If you have downloaded the installation files from openoffice.org then you have done it wrong.  You should not try to install programs the way you are used to doing in windows by downloading the installation files from the internet, but use the **software-center** or **synaptic** for that, which will download and install the packages from dedicated repositories.

Personally, I would suggest you forget openoffice and stick with libreoffice, but use the libreoffice ppa to install it.  See  [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) for all the information on using this.  Having added the ppa repository use synaptic to install libreoffice, but do not forget to reload the repositories first.

To keep all the configurations you have set up for OOo in LO, backup and then rename the hidden **.openoffice.org** folder in your home to **.libreoffice** by right clicking it in the right hand pane of nautilus and choosing rename, or with the command ```
cp -R .openoffice.org/ .openoffice.orgbak && mv .openoffice.org .libreoffice
```in terminal.

---

### Post by Macrotus on 2011-10-05
Hi

Thanks for your reply.

I'm trying to install OpenOffice from Synaptic, but I'm unlucky. I don't know what packages I should choose so it works. I also tried to install it through Software Center. For example I click OpenOffice Writer and install -> I got error "Package dependencies can't be figured" or something like that (I got that in a different language, so I can't be sure how it's said in English).

I downloaded LibreOffice from its website and installed. Now I have removed it through terminal.

Edit. Or is OpenOffice replaced with LibreOffice permanently?

And here's why I don't want to use LibreOffice: It looks too much Windows. I hate that Java look in the program.

---

### Post by Frogs Hair on 2011-10-05
> Or is OpenOffice replaced with LibreOffice permanently? 

Yes , but I think OO is still in the Lucid repository / software center because that's what it came with .

---

### Post by ajgreeny on 2011-10-05
OpenOffice is still in, and will remain in the lucid repos until lucid looses its support, I think, and if you don't enable the libreoffice ppa repos as I showed you, LO will not show at all in the packages available.

If you try to install libreoffice using the ppa while OOo is still installed in your system, you will be told that OOo has to be removed for the LO installation to proceed.  Just tick for the package **libreoffice** to be installed and all the dependencies will be included in the list automatically.

Finally, I do not understand what you mean by the comment > It looks too much Windows. I hate that Java look in the program.  In my system LO looks exactly the same as OOo did, but it is a bit faster, and is more up-to-date than the OOo  version available for lucid.

---

### Post by Macrotus on 2011-10-06
Yes, it told me to I need to remove OpenOffice to install LibreOffice. Well, I have nothing agains LibreOffice, but this look disturbs me.

[http://img189.imageshack.us/img189/3620/windows95lo.png](http://img189.imageshack.us/img189/3620/windows95lo.png)

OpenOffice looked like this

[http://i1-news.softpedia-static.com/images/extra/LINUX/large/openoffice3ubuntu810-large_005.png](http://i1-news.softpedia-static.com/images/extra/LINUX/large/openoffice3ubuntu810-large_005.png)

It is much better than that Windows 95 look in LibreOffice.

---

### Post by Macrotus on 2011-10-06
Well, I finally got OpenOffice installed, I only needed to uninstall all the programs I could found with searching for "libreoffice" in the software center.

Why apt didn't tell me which packages were incompatible?

Edit. ARRGGH!!!! When I installed OpenOffice again, I got the terrible horrible super über look there too! What should I do?

I want it to look this

[http://user.services.openoffice.org/en/forum/download/file.php?id=6744&mode=view](http://user.services.openoffice.org/en/forum/download/file.php?id=6744&mode=view)

This is what it was before...

---

### Post by Steeperton on 2011-10-06
Don't have Lucid anymore, but to integrate Libreoffice with the "non-Win 95" look you'll need libreoffice-gtk installed. Maybe there's an openoffice.org-gtk package or something?

---

### Post by Macrotus on 2011-10-06
Thanks! That is what I wanted, works perfectly!

Why shouldn't I use Lucid? It's the newest LTS, and it works a few years forward.

---

### Post by Steeperton on 2011-10-06
> **Macrotus said:**
> Thanks! That is what I wanted, works perfectly!

Why shouldn't I use Lucid? It's the newest LTS, and it works a few years forward.

Sorry, I meant *I* don't use Lucid anymore... For some reason, I missed out the "I" when typing it!:)

---

### Post by Macrotus on 2011-10-06
Okay! Task closed!

---

