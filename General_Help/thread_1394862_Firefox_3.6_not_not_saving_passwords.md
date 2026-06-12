---
title: "Firefox 3.6 not not saving passwords"
date: 2010-01-31
forum: General Help
---

### Post by motorcity909 on 2010-01-31
Hi there

Since the upgrade to 3.6 the list of sites that I had for Firefox ***not*** to remember the passwords for has been emptied. 

Most of them are sites that don't allow FF to even offer to save the password so they are fine but there is one site where everytime I visit it, it offers to save the password, I click 'never for this site', it is in the list of exceptions but the next time I go to the site, it asks again if I want to save it.

This never happened with 3.5 or earlier and it also seems to be fine on 3.6 on Windows machines (my son's XP FF 3.6 has that same site listed and successfully doesn't remember the password and it's still got all the other sites too).

The site in question is actually my router login page so can't give you the URL for anyone else to check it so this post is too see if anyone else has seen the same problem.

Cheers as always
Dave

---

### Post by lovinglinux on 2010-01-31
Export you passwords with [Password Exporter](https://addons.mozilla.org/en-US/firefox/addon/2848), then close Firefox and delete the files *signons.sqlite* and *key3.db* from your FF profile folder, then start Firefox and import the passwords back and setup the master password again if you have one. 

That should fix the problem.

---

### Post by motorcity909 on 2010-01-31
Thanks for the reply.  I'll give that a try later.

Interestingly, if I uncheck 'site preferences' from the Clear Recent History function then the exceptions seem to remain.  Once checked again and cleared, it removes those exceptions again.

That tip was from here - [http://forums.mozillazine.org/viewtopic.php?f=38&t=1716725](http://forums.mozillazine.org/viewtopic.php?f=38&t=1716725)

---

### Post by motorcity909 on 2010-01-31
Hi again

I followed the steps and at first all seemed well.  

I exported both my saved passwords and those sites disabled from saving.  

The latter file was (more or less) empty as the 'exceptions' box was empty but once I deleted those two files the exceptions box had the dozen or so sites I'd disabled; therefore I exported those again.

I then imported both lists again and first checked if it was offering to remember my router password - it didn't.:D

However, once I cleared history and re-opened FF, the exceptions list was empty again and it was asking if I wanted it to remember the router password.:cry:

Could it be that 'site preference' option I mentioned below?  I thought that just remembered if you'd zoomed text (amongst other things) on a website and it would remember for the next visit.

I suppose the important thing is it's remembering the saved passwords!

Maybe there are FF extensions for password management, I'll take a look.

---

### Post by lovinglinux on 2010-01-31
> **motorcity909 said:**
> Hi again

I followed the steps and at first all seemed well.  

I exported both my saved passwords and those sites disabled from saving.  

The latter file was (more or less) empty as the 'exceptions' box was empty but once I deleted those two files the exceptions box had the dozen or so sites I'd disabled; therefore I exported those again.

I then imported both lists again and first checked if it was offering to remember my router password - it didn't.:D

However, once I cleared history and re-opened FF, the exceptions list was empty again and it was asking if I wanted it to remember the router password.:cry:

Could it be that 'site preference' option I mentioned below?  I thought that just remembered if you'd zoomed text (amongst other things) on a website and it would remember for the next visit.

I suppose the important thing is it's remembering the saved passwords!

Maybe there are FF extensions for password management, I'll take a look.

Yes, I have checked the "Site Preferences" in the "Clear History" and indeed it deleted the exception list. So leave it unchecked and you should be fine.

---

### Post by motorcity909 on 2010-01-31
Thanks again LovingLinux

Do you think this counts as a bug and if so are Mozilla aware of it??

Out of interest, what gets saved by site preferences?

Thanks for all your help today,
Dave

---

### Post by lovinglinux on 2010-01-31
> **motorcity909 said:**
> Thanks again LovingLinux

Do you think this counts as a bug and if so are Mozilla aware of it??

I don't think it's a bug. It's just a different way of doing things. Mozilla has changed the way Firefox clears stuff when they released 3.5 and lot's of people got confused. Perhaps they should not include to many things on that tool or do not call it "Clear Recent History". IMO, would be more logical do have a button in the exception list to delete the selected entries.

> **motorcity909 said:**
> Out of interest, what gets saved by site preferences?

To be honest I had never explored t in deep, but I did some tests now and it deletes...

Exceptions - Cookies
Exceptions - Images (load images automatically exception list)
Allowed Sites - Pop-ups (pop-up exception list)
Allowed Sites - Add-on Installation (add-ons installation permission exception list)

Basic everything that has an Exception List button.

---

### Post by motorcity909 on 2010-02-01
All sorted now.  I'm no longer clearing site preferences and the disabled password sites are retained in the Exceptions and those sites are not prompting me to remember the password.

That plus sorting my Thunderbird [query]("http://ubuntuforums.org/showthread.php?p=8754865#post8754865") means it's been a good Mozilla day!

=D>

---

### Post by lovinglinux on 2010-02-01
> **motorcity909 said:**
> All sorted now.  I'm no longer clearing site preferences and the disabled password sites are retained in the Exceptions and those sites are not prompting me to remember the password.

That plus sorting my Thunderbird [query]("http://ubuntuforums.org/showthread.php?p=8754865#post8754865") means it's been a good Mozilla day!

=D>

Nice. I need to figure out Thunderbird is not deleting my imap messages from Gmail. It keeps downloading copies from the archives. ](*,)

---

