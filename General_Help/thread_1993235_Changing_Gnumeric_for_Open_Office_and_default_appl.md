---
title: "Changing Gnumeric for Open Office and default applications"
date: 2012-06-01
forum: General Help
---

### Post by zcacogp on 2012-06-01
Chaps, 

This must be a simple one, but I can't find the answer. 

I have installed Xubuntu 12.04 (having upgraded from Ubuntu, but not getting on with Unity or Gnome-Shell). I am used to Libre Office, so have installed it. I have also removed Gnumeric using the command:

# sudo apt-get remove --purge Gnumeric 

However, whenever I double-click on a *.ods file it won't open - I think it tries to open in Gnumeric but fails. If I right-click on it the first option is "Open with Gnumeric Spreadsheet", and the second is "Open with ...", and you can choose Open Office spreadsheet. 

This is a pain - I just want to double-click it to open in Open Office, and don't understand why it is still trying to open in Gnumeric. How can I change the preferred application for *.ods files? 

Thanks, in advance, for any help. 


Oli.

---

### Post by pbrane on 2012-06-01
You might try this:
[http://unix.stackexchange.com/questions/13748/fixing-mime-type-on-ubuntu]("http://unix.stackexchange.com/questions/13748/fixing-mime-type-on-ubuntu")

---

### Post by The Cog on 2012-06-01
right-click the file, choose **Properties** and change **Open With**. This changes the default application for all files of that type.

---

### Post by ajgreeny on 2012-06-01
I can't remember with certainty about thunar, but I think you can right click on an .ods or .odt file, choose Properties, and in that you can choose the application you want to use as default.

---

### Post by zcacogp on 2012-06-02
Chaps, 

Thanks for the answers ... just opening it once in OO didn't do it, but ajgreeny's answer (below) was spot on - thanks ajgreeny! 

pbrane - thanks for the link. Looks like that command may change a number of other things as well ... maybe I'll try it if other things seem to be wrong as well. 


Oli. 

> **ajgreeny said:**
> I can't remember with certainty about thunar, but I think you can right click on an .ods or .odt file, choose Properties, and in that you can choose the application you want to use as default.

---

### Post by pbrane on 2012-06-03
> **zcacogp said:**
> Chaps, 

...

pbrane - thanks for the link. Looks like that command may change a number of other things as well ... maybe I'll try it if other things seem to be wrong as well. 


Oli.

Yes that command resets all the mime types I think. Glad you got it working.

---

