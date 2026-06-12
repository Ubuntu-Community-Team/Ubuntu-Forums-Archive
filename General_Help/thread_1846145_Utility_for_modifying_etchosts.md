---
title: "Utility for modifying /etc/hosts"
date: 2011-09-18
forum: General Help
---

### Post by tnanek on 2011-09-18
I would essentially want to have [this program]("http://shades-of-orange.com/post.aspx?id=350b7e35-a75a-4029-b116-4bc54b49ace6"), but for the general non-windows device. Should such a thing exist, I'm just not finding it on Google.

My specific use case is I'm a web developer, and I'm trying to help a team of users to be able to preview my work on a separate production server. Now without the purchasing of another domain, I believe this requires writing a script to modify their hosts file to append my entry to it.

On checking the [Wikipedia page]("http://en.wikipedia.org/wiki/Hosts_file#Location_in_the_file_system")'s entry, the hosts file seems to generally be accessible in /etc/hosts (and I can manually handle situations where it isn't so - not a huge team). I've already written a script for Windows modification, using the program described in the first link and a batch file (yet to test though).

---

### Post by Dangertux on 2011-09-18
Honestly, it's very straightforward to edit your hosts file. I would consider just creating a simple bash script they could run that would do something like the following

```

echo "xxx.xxx.xxx.xxx        domain.com" >> /etc/hosts

```

where xxx.xxx.xxx.xxx is the ip of the server in question.  Then a simple script to remove it after the presentation is done, using sed would be fine for that.

---

### Post by tnanek on 2011-09-18
I just want to make sure they don't do that multiple times myself.

---

### Post by tnanek on 2011-09-18
Nevermind, I did it using if's and grep.

---

