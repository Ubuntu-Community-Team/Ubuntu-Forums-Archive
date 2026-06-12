---
title: "Prime user suddenly removed from admin group"
date: 2011-03-10
forum: General Help
---

### Post by henrylaw on 2011-03-10
Twice today, and several times recently, I have had a sudo command rejected with the dreaded message "<user> is not in the sudoers file..."  

It's because my user -- which is the main user, the one you create on Ubuntu installation -- has "fallen out of" the admin group.  I can fix it because there are other users defined which are still in the admin group and I can su to one of them and add myself back.

But why is it happening?  I'm doing software development, and use sudo mainly to do benign things like copying new versions of Perl programs into the application library: I'm not going anywhere near the security subsystem, for instance.  I'm worried that one day whatever-it-is will choose to drop all the users out of admin and then I'll have to resort to live CD hacking to fix it. 

I've searched for bugs and other forum reports without finding anything useful.  This is Ubuntu Server 64-bit 10.04.2 and patched monthly.

---

### Post by henrylaw on 2011-03-10
> **henrylaw said:**
> Twice today, and several times recently, I have had a sudo command rejected with the dreaded message "<user> is not in the sudoers file..."  

It's because my user -- which is the main user, the one you create on Ubuntu installation -- has "fallen out of" the admin group. ... snip

But why is it happening?

Well, I am embarrassed to report that the reason it's happening is, ahem, that I'm doing it myself.  (Somehow posting the question makes one think more about the cause ...)  I'll document it for others who might fall foul of the same thing.

More than once today I've had to add myself to other groups in the system and I did so with    usermod -G somegroup <my id>

But the list of groups in usermod -G is the _final list you want_, not just the name of the new group!  So each time I issued the above command I ended up in "somegroup" and no others.  

Now I'll crawl off and be embarrassed all on my own.:redface:

---

### Post by lithopsian on 2011-03-10
Yup, we've all done that one):P

---

### Post by henrylaw on 2011-03-10
For completeness I'll add that you should include the [FONT=Courier New][SIZE=2]-a[/SIZE][/FONT] flag on the [FONT=Courier New]usermod[/FONT] command; this _adds_ the named group and doesn't blat out all the others.

---

