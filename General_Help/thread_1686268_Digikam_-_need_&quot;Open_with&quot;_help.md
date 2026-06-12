---
title: "Digikam - need &quot;Open with&quot; help"
date: 2011-02-12
forum: General Help
---

### Post by cogier on 2011-02-12
I am trying to get Nautilus to open image files with Digikam.

I have opened Nautilus, right clicked on an image, selected **Open with > Other application **. What I need to know is what to put in the **Use a custom command** box. Putting **digikam** in the box does not work for me nor does selecting it from the **Open with** selection.

If you have Digikam on your computer and clicking on an image opens the image in Digikam can you tell me what is listed in your **Open with** box.

Thanks.

---

### Post by cogier on 2011-02-12
Bump

---

### Post by cottfcfan on 2011-02-12
Assuming you're using Ubuntu & not Kubuntu, choose a picture file, right click on the file, choose "properties" and across the top choose "open with" and check the Digikam box. If Digikam isn't in the list click the "add" button and locate it.
 Checking just one file will change the default for all your picture files, and jobs done.

ps don't bump so quickly, sometimes answers can take hours.

---

### Post by cogier on 2011-02-12
Thanks but I had done this. The right click shows "Open with digikam" - It just does nothing. I am using Ubuntu 10.04.

---

### Post by cottfcfan on 2011-02-12
In the "custom command" box, you could try /usr/bin/digikam

If that doesn't work you need to locate the path to execute digikam, but it is usually in /usr/bin.

---

### Post by cogier on 2011-02-13
Thanks cottfcfan you were correct in that /usr/bin/ is where the Digikam program is located but it still does not work.

I have installed Digikam on my laptop as well which is running 10.10 (my desktop is on 10.04) and the problem is exactly the same.

You click on a picture, it offers to open in with Digikam but nothing happens.

---

### Post by cottfcfan on 2011-02-13
Must have something to do with running a kde app in a gnome environment, I don't use Digikam I prefer Shotwell so I can't help any further, but i'm sure someone else must have the same problem.

---

### Post by cogier on 2011-02-19
Thanks for your help Cottfcfan. I appreciate the effort you put in. I am sorry that I "bumped" to quickly for your liking and will try to behave myself better in the future. (No Brownie points today then!)

Your thoughts on the fact that this could be a KDE, while I am using Gnome, issue is of interest and a possible reason for my problem. I would just say that if this is the case then this is another reason why Linux is held back from the main stream. 

It needs to work better. 

Having said that there are so many thing that work better in Linux than Windows.

I still have issues:-

How do I get Gnome to open a Digikam file automatically when I double click on a .jpg file?

Any help appreciated.

---

### Post by cottfcfan on 2011-02-20
Ok, I just looked at installing Digikam, but it means 125 packages & 100mb, which I do not want to do.
 Just see if the following works:
Go into your Home Folder, click edit/preferences/media.
Under "Photos" click "ask what to do", does Digikam appear there or under "open with other application"?

---

### Post by tredegar on 2011-02-20
You should try opening digikam from a terminal:
Open a terminal, type **digikam** then press RETURN.
You may see useful error messages in the terminal which will help you identify the problem.

---

### Post by cogier on 2011-02-20
I went to "edit/preferences/media" and selected photos and drilled down to usr/bin and selected digikam but still nothing happens when I click on a photo.

Typing digikam in terminal produces the following and the program runs OK (not sure what to make of the output).

charlie@XPS-M1330:~$ digikam
QSqlDatabasePrivate::removeDatabase: connection 'ConnectionTest' is still in use, all queries will cease to work.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kbuildsycoca4 running...
kbuildsycoca4(2030) KBuildMimeTypeFactory::createEntry: Missing <comment> field in "application/x-note.xml" 
kbuildsycoca4(2030) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/abiword.desktop" is not compliant with XDG standard (missing trailing semicolon). 
Time elapsed: 34 ms
Model: Time elapsed: 82 ms
TextureColorizer: Time elapsed: 15 ms
Time elapsed: 3 ms
Model: Time elapsed: 22 ms

---

### Post by tredegar on 2011-02-20
> 
Typing digikam in terminal produces the following and the program runs OK (not sure what to make of the output).
There are errors (as listed).

To my mind, KDE4 is broken, which is why I no longer use KDE.

But it seems you have found a way to run the application you want.

So maybe that's OK ?

---

