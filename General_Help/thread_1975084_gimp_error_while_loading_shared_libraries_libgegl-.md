---
title: "gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared obje"
date: 2012-05-06
forum: General Help
---

### Post by Senior_Buckethead on 2012-05-06
I installed gimp, but it wouldnt start. So I ran it from the command line and got the following errors:
```

glenn@acer:~$ gimp
gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory
glenn@acer:~$

```

I then ran dpkg to isolate the error:
```

glenn@acer:~$dpkg -l gimp
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gimp           2.6.12-1ubuntu The GNU Image Manipulation Program
glenn@acer:~$ 

```
What is the error? How can I fix it?

---

### Post by Senior_Buckethead on 2012-05-06
Solved the problem. Ran the following:
```
 [COLOR=Black][COLOR=red]
sudo apt-get update[/COLOR][/COLOR][COLOR=Black][COLOR=red]
sudo apt-get purge gimp libgegl* libbabl*[/COLOR][/COLOR][COLOR=Black][COLOR=red]
sudo apt-get install gimp[/COLOR][/COLOR][COLOR=Black][COLOR=red]
sudo apt-get clean[/COLOR][/COLOR]

```

That fixed it.

See:[http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html](http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html)

---

### Post by vangop on 2012-06-01
Same error, but this solution is (recommended everywhere) won't work. Still get the same problem after the reinstall.

---

### Post by Senior_Buckethead on 2012-06-01
Have you tried going to synaptic and manually finding and removing the packages, if apt wont do it?

---

### Post by cirosantilli on 2012-06-01
This was not working for me either, I had to first REMOVE the old gimp mathaeus ppas (I'm on Ubuntu 12.04):

```
cd /etc/apt/sources.list.d/
sudo rm matthaeus123-mrw-gimp-svn-precise.list matthaeus123-mrw-gimp-svn-precise.list.save
```Then remove Gimp and reinstall as indicated on the above answers:

  ```
sudo apt-get remove gimp
sudo apt-get update
sudo apt-get purge gimp libgegl* libbabl*
sudo apt-get autoremove
sudo apt-get install gimp
```Don't ask me why it worked...

---

### Post by cirosantilli on 2012-06-01
sorry duplicated post

---

### Post by Senior_Buckethead on 2012-06-01
Your right that does work. Now Il start loading extras on to see what was the culprit.

And I have a fix that will install Gimp 2.8 from ppa. You dont need to uninstall the old version of gimp first.
```

[COLOR=red][FONT=monospace]sudo add-apt-repository ppa:otto-kesselgulasch/gimp[/FONT][/COLOR][COLOR=red][FONT=monospace]
sudo apt-get update[/FONT][/COLOR][COLOR=red][FONT=monospace]
sudo apt-get install gimp[/FONT][/COLOR][COLOR=red][FONT=monospace]
sudo apt-get install gimp-plugin-registry[/FONT][/COLOR]

```Here is the reference: [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html).

The only thing that I found I had to do was delete the gimp desktop icon that I had dragged from the  menu, and drag the new icon from menu to the desktop (if you want desktop icons like me). It will run from the menu icon and also from command line.

Happy gimping.

---

### Post by bjverde on 2012-06-04
> **cirosantilli said:**
> This was not working for me either, I had to first REMOVE the old gimp mathaeus ppas (I'm on Ubuntu 12.04):

```
cd /etc/apt/sources.list.d/
sudo rm matthaeus123-mrw-gimp-svn-precise.list matthaeus123-mrw-gimp-svn-precise.list.save
```Then remove Gimp and reinstall as indicated on the above answers:

  ```
sudo apt-get remove gimp
sudo apt-get update
sudo apt-get purge gimp libgegl* libbabl*
sudo apt-get autoremove
sudo apt-get install gimp
```Don't ask me why it worked...

Thanks, Cirosantilli.

Its works for me

Ubuntu 12.04
GIMP 2.6

---

### Post by metodiew on 2012-06-13
> **cirosantilli said:**
> This was not working for me either, I had to first REMOVE the old gimp mathaeus ppas (I'm on Ubuntu 12.04):

```
cd /etc/apt/sources.list.d/
sudo rm matthaeus123-mrw-gimp-svn-precise.list matthaeus123-mrw-gimp-svn-precise.list.save
```Then remove Gimp and reinstall as indicated on the above answers:

  ```
sudo apt-get remove gimp
sudo apt-get update
sudo apt-get purge gimp libgegl* libbabl*
sudo apt-get autoremove
sudo apt-get install gimp
```Don't ask me why it worked...

It works for me too. Thanks! :-)

Ubuntu 12.04

---

### Post by neo1691 on 2012-07-13
Help me too!! Ubuntu 12.04!! What must have caused the problem in the first place??

---

### Post by blackstripes on 2012-07-25
Worked for me as well, thanks!

---

