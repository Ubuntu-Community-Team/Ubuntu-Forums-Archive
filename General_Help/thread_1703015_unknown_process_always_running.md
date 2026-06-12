---
title: "unknown process always running"
date: 2011-03-08
forum: General Help
---

### Post by vafred69 on 2011-03-08
Maybe someone can shed some light on this process that is running. It is using my CPU about 100% since there are 2 instances of it running with about 50% used by each.

abc_sieve_2.10_i686-pc-linux-gnu

I've never noticed it running before and don't think I've installed anything except updates.

Any help would be appreciated.

Thank you all!!!!

---

### Post by bab1 on 2011-03-08
> **vafred69 said:**
> Maybe someone can shed some light on this process that is running. It is using my CPU about 100% since there are 2 instances of it running with about 50% used by each.

abc_sieve_2.10_i686-pc-linux-gnu

I've never noticed it running before and don't think I've installed anything except updates.

Any help would be appreciated.

Thank you all!!!!

That looks to be from the ABC@home project.  

"ABC@home is an educational and non-profit distributed computing project finding abc-triples related to the ABC conjecture."  

See [**_here_**]("http://abcathome.com/").

---

### Post by mmsmc on 2011-03-08
how could it get on his computer?

---

### Post by vafred69 on 2011-03-08
> **bab1 said:**
> That looks to be from the ABC@home project.  

"ABC@home is an educational and non-profit distributed computing project finding abc-triples related to the ABC conjecture."  

See [**_here_**]("http://abcathome.com/").
Hmmmm...

OK I see that it is from a package named BOINK. Where would it come from? I checked the repositories and cannot find anything about it.

Is it necessary and if not how to remove whatever is using it?

Thank You!!

---

### Post by bab1 on 2011-03-08
> **vafred69 said:**
> Hmmmm...

OK I see that it is from a package named BOINK. Where would it come from? I checked the repositories and cannot find anything about it.

Is it necessary and if not how to remove whatever is using it?

Thank You!!

It is not part of the OS and I don't see a BOINK package either.  Where did you see it as a .deb package?

It looks like the correct name is BOINC.  From the web page > BOINC is a program that lets you donate your idle computer time to science projects like SETI@home, Climateprediction.net, Rosetta@home, World Community Grid, and many others. 

Did you install any of these?

Edit:  Here is what UC Berkley says about [**_BOINC on Ubuntu_**]("http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu").

---

### Post by vafred69 on 2011-03-08
OK Solved!!

Went to Package Manager and removed boinc-client

I have no idea where it came from but if anything nasty happens I'll repost.

Thanks for all the help.

---

### Post by vafred69 on 2011-03-10
> **bab1 said:**
> It is not part of the OS and I don't see a BOINK package either.  Where did you see it as a .deb package?

It looks like the correct name is BOINC.  From the web page 

Did you install any of these?

Edit:  Here is what UC Berkley says about [**_BOINC on Ubuntu_**]("http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu").
I don't know where it came from but now I'm glad it's gone.

Thanks Everyone for the Help

---

