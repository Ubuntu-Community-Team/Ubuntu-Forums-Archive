---
title: "Ideas for a simplistic network needed"
date: 2012-02-15
forum: General Help
---

### Post by iangarforth on 2012-02-15
Hi all,

I suppose what I'm after is ideas, if I can..?

I have an opportunity to try to convince folks at my school that Ubuntu might be the way forwards.  Accordingly, I seem to be being given the chance to run 15 or so 'legacy' laptops on an Ubuntu system to show what it can do.

The rest of the school currently runs on an XP based network.  I can really run this any way I see fit, but I'm interested to see what people think might be the best route forwards.

Having got my netbook running 11.10 working essentially fine on the school network, I'm keen to - in general - push the idea of cloud-based working.  It seems to me that this approach might minimise the complexity of Ubuntu file servers, etc, that lie rather beyond the scope of what I want to achieve.

That said, the Dropbox-style client might not work either - I can't be having it allocating 2GB of storage on each machine for all of 600 students.

In a perfect world, I'd like students to be able to access the internet, access their cloud-based files through some sort of vaguely easy-to-use interface, and be able to print.  I think I can achieve the first and the last, but I'm not sure how t best achieve the middle without lots of redundant local duplicated files.

Also, it seems to me that this model can be essentially serverless.  Accordingly, I presume I then build a 'guest' account with the access that I want on a particular machine, but how do I then propagate this account/these settings to the other 14 machines?

For what it's worth, this idea of a single user being used by multiple users has had some precedence in the school - in our Mac suite, for example, all users log on with a generic username, though there, they sit at the same machine, and so get access to previous work that way.  I'd like to find a more elegant solution.  In some ways, it's not ideal - I appreciate there's some cost in accountability, but a corresponding benefit in simplicity.

Any thoughts or observations would be very gratefully received!

---

### Post by dcstar on 2012-02-16
[http://www.pwpc.net/blog/?p=194](http://www.pwpc.net/blog/?p=194)

---

### Post by Khayyam on 2012-02-16
iangarforth ...

I have some experience with this (though not with Ubuntu, but that shouldn't matter). I have migrated whole deparments within a 40,000 student university, and provided a "proof of concept" prior to the work proceeding. The university is divided with many departments and student levels each of which is compartmentalised in terms of access.

Some pointers:

You need to work from the botom up, not the top down. The client is not really the issue, its how to merge with the currently existing system. How do students currently authenticate (LDAP?), and does the authentication system cover all services? Are staff/students provided with networked storage (CIF/Samba, AppleTalk). Once you've figured out how the current NT/XP system is setup, you can see in what ways your laptops can be intergrated with these services.

If your XP users are authenticated via LDAP your clients can also use LDAP for authentication (no 'accounts' on the laptops) and query the LDAP for 'shares' for that user, even mount them as $HOME. Other services, such as printers, can also be configured this way, or 'autodetected'.

You need to avoid doing anything with the user setup, you need to approch this not as you would a 'personal computer' or your own Ubuntu install, but a machine configured to do most of this on its own using what services are avilable on the network.

If the staff/students are also using some form of calendar, mail, or whatever, then these should also be accessable (and preferably authenticated at login).

As far as "wowing" the "folks at school" ... mostly its about seemless migration, "cool features" are generally less impressive. In my experience it really came down to money, when six year old hardware suddenly became useable again and the cost amounted to basically two peoples labour, that was the "wow" moment.

HTH ...

---

