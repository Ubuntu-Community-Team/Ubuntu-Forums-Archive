---
title: "Eclipse updates not working"
date: 2012-05-01
forum: General Help
---

### Post by sixcorners on 2012-05-01
I installed eclipse and I went to "Check for Updates." After I completed the wizard it was installing some updates but it failed: ```
An error occurred while uninstalling
session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.p2.engine.phases.Uninstall, operand=[R]org.eclipse.platform_root 3.7.2.dist-9nF7UHagFqn9pElwWhC90gLz-soEuSGYmtSeiRH --> null, action=org.eclipse.equinox.internal.p2.touchpoint.natives.actions.CleanupzipAction).
Backup of file /usr/lib/eclipse/.eclipseproduct failed.
File that was copied to backup could not be deleted: /usr/lib/eclipse/.eclipseproduct
```So I go to try it as root. Now the update sites are different and it can't find any updates.
Here are the sites running as root:
> [http://download.eclipse.org/releases/helios](http://download.eclipse.org/releases/helios)
[http://download.eclipse.org/eclipse/updates/3.6](http://download.eclipse.org/eclipse/updates/3.6)Here are the sites running as a normal user:> [http://download.eclipse.org/technology/epp/packages/indigo/](http://download.eclipse.org/technology/epp/packages/indigo/)
[http://download.eclipse.org/technology/epp/packages/indigo/R/](http://download.eclipse.org/technology/epp/packages/indigo/R/)
[http://download.eclipse.org/releases/indigo/](http://download.eclipse.org/releases/indigo/)It seems there are two problems here, first that updating as a normal user doesn't work and second that the list of update sites enabled by default are different for the root user and a normal user. Eclipse says it is version 3.7.2.
By the way, what is the difference between these update sites? Why isn't there just one for each version of Eclipse?

---

### Post by brainwash on 2012-05-02
Normal users can't modify the program files of Eclipse, thus updating the core components does not work, because they are owned by root. These updates should be managed by Ubuntu.

If you run eclipse as normal user and install plugins via the Eclipse Marketplace or from a websites, they will get saved in your HOME folder (together with user-specific program settings including a separate update site list). These plugins can be easily updated by using the eclipse update routine.

Alternative method:
Download the tar.gz package from the Eclipse website and extract it in your HOME folder. This allows updating of all components without root privileges.

Eclipse 3.6 = Helios
Eclipse 3.7 = Indigo

---

### Post by sixcorners on 2012-05-04
That's fine and all but the problem remains. I, as a normal user, can't update eclipse because of that error I quoted and root has strange update sites. Thanks for the reply by the way.

---

### Post by caliverse on 2012-05-13
So why doesn't eclipse running as root have any update repositories listed for Indigo, only Helios?

Maybe the newer updates would fix the problem with the Help index :razz:

---

### Post by zinglax on 2012-05-14
Hey I'm having these troubles too.  I was developing for android and I wanted to debug on my phone (which I have done before with no problems) but the sdk was not recognizing it.  I had it working on 11.10 but then updated to 12.04 and haven't had any success debugging from my phone, not sure if this was the source of the problem.  I tried to get updates for eclipse and that's when I got the same error in the original post.

Any thoughts?

P.S. Has anyone been able to debug from their android phone on 12.04?

Thanks

---

### Post by vsinha on 2012-08-30
I encountered the error while installing Google app engine. Having read this thread, I started eclipse as root user, and copied the same site address into the "work with" bar. It worked and now it is working fine even when run as a normal user.
If the repositories are not listed while running as root just copy the address of update sites an paste it into "work with" bar while running as root.

---

### Post by impliu on 2012-10-31
I have the same problem, I add the  nomal user mode update sites ([http://download.eclipse.org/releases/indigo/](http://download.eclipse.org/releases/indigo/)
  and [http://download.eclipse.org/releases/indigo/201202240900](http://download.eclipse.org/releases/indigo/201202240900)) in root mode 
site list, and update ok.
Thank you!

---

