---
title: "gnome-do email failure"
date: 2010-12-02
forum: General Help
---

### Post by dre12b on 2010-12-02
I can no longer launch an email to a contact from gnome-do.  I select a contact (using Gmail Contacts plugin) in the first pane, "Email" in the second pane, hit return and get nothing.  

I use Evolution as my email client because I like the tight integration with the gnome desktop.  Previously, in Lucid 10.04 if I'm remembering correctly, this action in Gnome-Do would launch an Evolution email window with the To: field already populated.

I'm running 32-bit 10.10 Maverick.  Anyone else having this issue?

Evidently there was a similar bug for Thunderbird that has been fixed.  [http://ubuntuforums.org/showthread.php?t=1472767](http://ubuntuforums.org/showthread.php?t=1472767)

And something similar when using chrome as preferred email client: [http://ubuntuforums.org/showthread.php?t=1522631&highlight=gnome-do+email](http://ubuntuforums.org/showthread.php?t=1522631&highlight=gnome-do+email).

---

### Post by ben2 on 2010-12-28
Same Problem here.
Launching gnome-do from terminal, yields the following:

> (Do:15054): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
Could not locate Tomboy on D-Bus. Perhaps it's not running?If I start tomboy manually, the last error message doesn't show up again.

If I try to open my mail client using gnome-do, typing "ben2 <tab> mail", I get the following problem: 
> Errore nel mostrare l'URL: Errore nell'eseguire lo stat del file "/home/ben2/xdg-email  'ben2@ben2.it'     ": File o directory non esistenteWhich means something like... "error resolving url: error determining the status of the file... file or directory doesn't exist.

Well, for sure /home/ben2/xdg-email doesn't exist... well, just changing directory doesn't help:
> ben2@galileo:~$ cd /usr/bin
ben2@galileo:/usr/bin$ gnome-do #now I try to write an email  typing "ben2 <tab> mail"
Errore nel mostrare l'URL: Errore nell'eseguire lo stat del file "/usr/bin/xdg-email  'ben2@ben2.it'     ": File o directory non esistente
Of course /usr/bin/xdg-email  does exist, executing manually "/usr/bin/xdg-email  'ben2@ben2.it'     " works perfectly fine. 

Does anybody else have the same problem?
I'm experiencing this with 10.10 on 64bit.

Best wishes!
ben

---

### Post by dre12b on 2010-12-28
Ben, I haven't gotten any insights into the Gnome-Do problem.  Seems like development has come to a screeching halt on the project.  A shame considering it is so fully featured.

I've started using Kupfer, which has a pretty great base of plugins available.  And email launching works with evolution.    

Synapse is a new project which seems to be generating a lot of energy.  I barely tested it, but couldn't get used to the non-pane based interface.  However, it evidently boasts some interesting new features due to its tight integration with zeitgeist.  [http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/](http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/)

---

### Post by begtognen on 2011-04-21
Dre12b - Thank you! I hadn't heard of Kupfer, and on your recommendation have given it a try. It works beautifully with Thunderbird. *So* pleased.

---

### Post by dre12b on 2011-04-21
Yes - Kupfer is keeping my very happy, too.  Glad you found it helpful.  

I recently upgraded Kupfer from it's PPA and the latest version rocks - even more plugins and an interface that is easier on the eyes.

---

