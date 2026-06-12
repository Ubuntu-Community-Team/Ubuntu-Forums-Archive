---
title: "firefox not responding"
date: 2009-07-14
forum: General Help
---

### Post by raymondvillain on 2009-07-14
I shut down jaunty with some firefox windows still active.

Upon re-boot, no fire fox (usually they're still there, the tabs are at the bottom of the screen) and when I click on firefox it hangs and will not load.

I renamed ~/.mozilla/firefox to ~/.mozilla/firefox.bak and tried again, but no improvement was observed.

I opened Nautilus with super user priveleges (gksudo nautilus) and in the terminal window this message appeared:

> $ gksudo nautilus
--- Hash table keys for warning below:

--> file:///~/.mozilla

--> file:///~/.mozilla/firefox

--> file:///
--> file:///~/.mozilla/firefox/904k6076.default/bookmarkbackups

--> file:///~/.mozilla/firefox.another_bak/ehbpwlm7.default

--> file:///~/.mozilla/firefox/904k6076.default

--> file:///root

(nautilus:4294): Eel-WARNING **:
 "nautilus-metafile.c: metafiles" hash table still has 7 elements at quit time (keys above)
(nautilus:4294): Eel-WARNING **:
 "nautilus-directory.c: directories" hash table still has 7 elements at quit time

I don't know what to make of this.

What is a hash table and how does one clear it?

---

### Post by lovinglinux on 2009-07-14
> **raymondvillain said:**
> I renamed ~/.mozilla/firefox to ~/.mozilla/firefox.bak and tried again, but no improvement was observed.

Have you done that after closing Firefox?

Go to the System Monitor and kill all firefox processes. Then rename ~/.mozilla/firefox

If that doesn't help, go to "System >> Adminsitration >> Synaptic Package Manager", search for Firefox, then select the package firefox-3.0, mark for reinstall and click apply.

I also recommend reading [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by raymondvillain on 2009-07-15
Thanks, lovinglinux.

I tried all that after closing firefox.

In system monitor, there were no firefox processes to kill.

I followed your instructions and re-installed firefox.

The problem still exists.  When I click on firefox, the following appears:

> Close Firefox
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.


I thought I would look around the file system to see if I could find anything helpful, and this is the result:

> ~$ gksudo nautilus

** (nautilus:3773): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: unknown format for key 'myshare/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

--- Hash table keys for warning below:
--> file:///root
--> file:///

(nautilus:3773): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:3773): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time

If I open a terminal window, and type:

> gksudo firefox

then the browser opens up normally.  No messages or problems.

What is causing all these "hash table" messages?

I am reading the tutorials you suggested, thanks for your help.

---

### Post by lovinglinux on 2009-07-15
I see, it's a permission problem.

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by raymondvillain on 2009-07-15
And thanks to you, lovinglinux, for fixing my Firefox troubles.  I followed the directions in the tutorial, removed the existing .mozilla/firefox directory, and firefox now starts normally.

I still have one problem, and that is with the "hash table" messages that appear when I open nautilus:

> gksudo nautilus

Nautilus-Share-Message: unknown format for key 'myshare/usershare_acl' as it contains 'Everyone:F,'.
Assuming that the share is read-only
--- Hash table keys for warning below:
--> file:///root

(nautilus:3457):
Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:3457):
Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

Maybe I'll post this in another forum as it is not a firefox sort of issue, but if anybody can shed some light on the matter I would appreciate it.

---

