---
title: "Made a major mistake..."
date: 2009-12-03
forum: General Help
---

### Post by LiNuXaDDiKt on 2009-12-03
Hi all,

I'm not really happy about my self...

Yep I did it...  Running any script as root is really not a good idea...

While giving a try to the Symfony PHP Framework, I ran a command which for some reason corrupted some of my system libraries.

It happened while I made a mistake in one of the config file of the Symfony package and it looks like it found a way to my system libraries.

[COLOR="Blue"]Now, is there a way to check all system files versioning integrity?[/COLOR]  Kind of like validating against the latest file versions?

Thanks god I had a couple of month old backup and I have been able to restore the libraries I think got corrupted.

Many services stopped like Bind, Apache, etc...

After restoring those libraries I've been able to restart those 2 services but I'm really scared of restarting the server without checking its full integrity.

---

