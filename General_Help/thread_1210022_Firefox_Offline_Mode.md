---
title: "Firefox Offline Mode"
date: 2009-07-10
forum: General Help
---

### Post by mthalis on 2009-07-10
I install apache2 using package manage. if i typed [http://localhost/](http://localhost/) it gave massage call "it works" and work well, if remove my Internet connection type [http://localhost/](http://localhost/) ,instated of that massage Firefox give this massage 
> Offline Mode
Firefox is currently in offline mode and can't browse the Web.

Then i run it another Firefox(download from Firefox site Firefox.tar.bz2) then work fine and give correct message.

I want to run apache in default Firefox without Internet how can i fix it.

---

### Post by phillw on 2009-07-10
> **mthalis said:**
> I install apache2 using package manage. if i typed [http://localhost/](http://localhost/) it gave massage call "it works" and work well, if remove my Internet connection type [http://localhost/](http://localhost/) ,instated of that massage Firefox give this massage 


Then i run it another Firefox(download from Firefox site Firefox.tar.bz2) then work fine and give correct message.

I want to run apache in default Firefox without Internet how can i fix it.


within firefox, click on File -->> Work Offline

That will toggle firefox between local-host & internet.

I just got used to clicking it, there *may* be a way of defaulting to it, but, heck, it's one click away !!!!

Regards,

Phill.

---

### Post by mthalis on 2009-07-10
Seems to be it's working thank phillw.

---

### Post by Sepero on 2010-06-16
Type about:config in the address bar, then set
toolkit.networkmanager.disable = true

---

### Post by xovertheyearsx on 2010-08-06
I'm have the same problem (v. Ubuntu 10.04), the only difference is that it still doesn't work in offline mode... its seems to be the issue with every browser... i get this response if i'm offline: 

The webpage at [http://localhost/](http://localhost/) might be temporarily down or it may have moved permanently to a new web address.

Here are some suggestions:
Reload this web page later.
  More information on this error
Below is the original error message

Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found.

Can't seem to figure it out.

---

