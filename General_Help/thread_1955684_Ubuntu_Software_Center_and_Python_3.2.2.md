---
title: "Ubuntu Software Center and Python 3.2.2"
date: 2012-04-09
forum: General Help
---

### Post by FatFrog on 2012-04-09
Now that I've started to get the hang of the basics, I decided to teach myself Python. I downloaded and installed IDLE, and upgraded my Python version to 3.2.2 from 2.7.2
Shortly thereafter, I tried to run the Ubuntu Software Center and nothing happened. It didn't start or throw an error or anything. I reverted back to 2.7.2 and was able to get the software center up and running.
My questions are:
1) Can anyone verify if there is some sort of known conflict with Python v3.2.2 and the Ubuntu Software center v5.0.6?
2) Does anyone know what substitutes for the Ubuntu Software Center work well with Python 3.2.2?

Switching back and forth isn't such a big deal for now, but I see it getting annoying if I have to keep doing it...

---

### Post by oldfred on 2012-04-10
Did you uninstall python 2.7? 
That breaks much of Ubuntu as it uses that version internally for more than just Software Center.

It used to be that you had to reinstall Ubuntu as nothing worked, but somethings still do. It may have uninstalled lots of applications that depend on 2.7 also, did you get everything back?

You can have both python versions installed and just have to specify python3 when you want to use the newer version.

---

### Post by FatFrog on 2012-04-10
I installed 3.2.2 along side the existing 2.7.2 installation. 
Then I ran the command:
#rm /usr/bin/python
Then I re-linked the /usr/bin/python folder to /usr/bin/python3
#ln -s /usr/bin/python /usr/bin/python3

 (I think that's the folder it was installed in)
I switch back to 2.7.2 with the command:
#ln -s /usr/bin/python /usr/bin/python2.7

Is that the recommended method?

---

### Post by oldfred on 2012-04-10
No, you need to leave 2.7 linked to python. 

Then you have a link to the current version of python3 to python3.

To start python3 you just type python3 instead of python. or in a file the first line is:

#!/usr/bin/python3
instead of 
#!/usr/bin/python

---

### Post by FatFrog on 2012-04-11
that sounds logical. Wish I knew that before. 
Thank you much...

---

