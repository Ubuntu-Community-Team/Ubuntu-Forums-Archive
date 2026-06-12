---
title: "Using variables in hostname"
date: 2010-03-31
forum: General Help
---

### Post by tturner226 on 2010-03-31
I'm rather new to Ubuntu and have been tasked with created a base Ubuntu image that can be used for cloning to multiple machines. As this is a network environment, each hostname will obviously need to be unique. Rather than manually changing the hostname each time a new, cloned machine is rolled out, I was wondering if there is a way to use a variable in the hostname (i.e., use a variable to truncate the the last 6 digits of the MAC address to the end of the static hostname--or any other unique variable for that matter--so it would look like hostname00E6D4). I appreciate your help.
 
Thanks.

---

### Post by john newbuntu on 2010-04-01
Would you rather use generic names as hostnames -such as names of trees, birds, comic characters, stars etc.  Might be meaningful.  You would have to do that manually though, although you could connect to a central DB(say mysql) and pick a name from there.

---

### Post by tturner226 on 2010-04-01
Unfortunately, no.  It's for a large corporation (700+ machines) that has a set naming convention.  They're named by department, so the naming convention for hostnames would be DEPARTMENTXX where XX is the truncated portion to give it a unique hostname.

---

### Post by john newbuntu on 2010-04-02
Well, in that case, I think it would make sense to include the name of the corporation (or it abbreviation) in the hostname and then a unique running sequence number.  The sequence number part of it is going to be the hard part especially using the cloning technique.

But as you mentioned, you can device a hash algorithm by inspecting the MAC id of each machine.  That would make things simple.

The other option as I mentioned beforeis to store a sequence number table in the database(file based or any other) and append it to the company name. Obviously the sequence number needs to be incremented with every read.

---

