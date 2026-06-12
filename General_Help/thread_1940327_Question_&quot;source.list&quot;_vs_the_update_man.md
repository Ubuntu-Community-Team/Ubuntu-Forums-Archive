---
title: "Question: &quot;source.list&quot; vs the update manager sources"
date: 2012-03-13
forum: General Help
---

### Post by Sosigene on 2012-03-13
Hello everyone,

I would like to understand something: 

Why, when I add new sources/repositories in update manager (for example ppa:n-muench/vlc or ppa:kubuntu-ppa/backports), are they not also listed in /etc/apt/sources.list?

Does that means that the update manager is using a different source/repository list than apt-get?
Does that mean that a system update via the update manager will give different results than a "sudo apt-get dist-upgrade" ?


thanks a lot! :)

Using: Ubuntu 11.10  i386

Sosigene

---

### Post by Cheesemill on 2012-03-13
Have a look in /etc/apt/sources.list.d/
Anything in that folder gets parsed along with /etc/apt/sources.list

(I think that's the correct directory name, I'm not on my Ubuntu box at the minute)

---

### Post by Sosigene on 2012-03-13
Ahhh!
thanks a lot Cheesemill!

Do you have any idea why they are separated like that?
Granted, it is one of those "why" question... :)

thanks a lot

Sosigene

---

### Post by Cheesemill on 2012-03-13
I think it just makes it easier for applications to add and remove repos, they can just create or delete a file instead of having to parse sources.list and add/remove lines from it.

It happens with a lot of configuration files, every directory on your system that ends with .d works in the same way, for example /etc/apache.conf and /etc/apache.conf.d/ etc...

---

### Post by Sosigene on 2012-03-13
ok, it makes sense...

thanks again Cheesemill

I consider this thread close

---

### Post by devinwhite717 on 2012-03-20
Use synaptic it will update all the necessary files

---

