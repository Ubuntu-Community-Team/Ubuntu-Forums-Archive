---
title: "&quot;Open as Administrator&quot; in Nautilus under Karmic"
date: 2010-04-21
forum: General Help
---

### Post by tperwez on 2010-04-21
Hi Folks,

This might be stupid question, yet I have no clue as to how to do it. I installed Ubuntu 9.10,  and under Nautilus, I want to open some folder(s) as administrator. In Ubuntu 8.10, I just used to click the right mouse button on the folder and this used to be one of the options. There is no such option available under 9.10. How can I do this in Nautilus?

Regards.

---

### Post by Directive 4 on 2010-04-21
in the terminal

gksudo nautilus

---

### Post by tperwez on 2010-04-21
> **Directive 4 said:**
> in the terminal

gksudo nautilus

I got the following errors after using this command:


** (nautilus:18795): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:18795): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:18795): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



It does not ask for password at all, just generates the above errors.

Something wrong?

Please help since I need to do some administrative work on this thing and cannot get started. Best.

---

### Post by Directive 4 on 2010-04-21
yea, umm, 

could try 

sudo nautilus


mine generates the similar error messages but launches nautilus as root.




(nautilus:6026): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:6026): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:6026): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:6026): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:6026): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

(nautilus:6026): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Shutting down nautilus-gdu extension

---

### Post by tperwez on 2010-04-21
Thanks again for the response. Mine did actually open nautilus as root but these errors and warnings do not belong in a good linux. I am so surprised as others have had similar problems for a long time and there seems to be only guesswork as to what to do. Why does the right mouse click not work as it used to?

Furthermore, using

gksuod nautilus

leaves the Terminal being used by the stupic nautilus and you cannoot use it without first closing the nautilus. Makes no good sense at all

BTW, 

sudo nautilus 

is not going to do anything.

---

### Post by 3rdalbum on 2010-04-21
What you want is the 'nautilus-gksu' package from Synaptic.

---

### Post by Directive 4 on 2010-04-21
> **tperwez said:**
> 

leaves the Terminal being used by the stupic nautilus and you cannoot use it without first closing the nautilus. Makes no good sense at all

BTW, 

sudo nautilus 

is not going to do anything.


you could fork the process to the background, or just open another terminalo,

also, 

just try sudo nautilus, 

it works, just not advised.

cool

---

### Post by tperwez on 2010-04-21
> **3rdalbum said:**
> What you want is the 'nautilus-gksu' package from Synaptic.

Thanks for the tip. I will install this package. Loks like I need it. Regards.

---

### Post by tperwez on 2010-04-21
Launching the 

gksudo nautilus &

is certainly netter. Thanks.

---

### Post by scouser73 on 2010-04-22
What I've done to open Nautilus as Administrator is to create a custom application launcher and place it on my panel.

**1** - Right click on panel and select **Add To Panel**

**2** - Select **Custom Application Launcher** on the screen that follows & click **Add**

**3** - In the Name field call it something like Nautilus As Root (or what ever)

**4** - In the Command field enter **gksudo nautilus**

In the comment field you can leave it blank if you wish as it's not necessary to fill that part in.

---

### Post by tperwez on 2010-04-22
> **scouser73 said:**
> What I've done to open Nautilus as Administrator is to create a custom application launcher and place it on my panel.

**1** - Right click on panel and select **Add To Panel**

**2** - Select **Custom Application Launcher** on the screen that follows & click **Add**

**3** - In the Name field call it something like Nautilus As Root (or what ever)

**4** - In the Command field enter **gksudo nautilus**

In the comment field you can leave it blank if you wish as it's not necessary to fill that part in.


I appreciate your advice and will try to set up my system accordingly.

And what about those errors and warnings? The fact that nautilus is supposedly the default gui environment for gnome, the idea that one has to download/install/configure something to get around these errors is not a good thing in my opinion. If one was trying to do something that is not a default operation, that I could understand.

I still do not like to open the nautilus as an administrator; I would very much have liked to obtain the same behavior as I had with 8.10. That allowed me to just open a given directory and its subdirectories as administrator. 

Regards.

---

### Post by oldos2er on 2010-04-22
I think those errors can be ignored.

As was mentioned, install nautilus-gksu to enable the right-click menu 'Open as Administrator'.

---

