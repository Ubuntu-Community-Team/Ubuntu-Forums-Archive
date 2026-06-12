---
title: "WebDAV and XP?"
date: 2010-07-27
forum: General Help
---

### Post by KevinCole on 2010-07-27
I have WebDAV set up, and working a la cadaver.  However, I'm trying to get it to integrate with a Windows XP system's Network Places.

[http://ubuntuforums.org/showthread.php?t=141263](http://ubuntuforums.org/showthread.php?t=141263)
appears to no longer be correct.

Thousands of solutions on the interwebs, none of which appear to be correct.

Failures:
[LIST]
[*]A straight URL gives a dialog box that asks for a username and password. Username gets munged into \\domain\username. Fail.
[*]Changing the URL to **[FONT="Courier New"]http://username@host.domain.tld/directory/[/FONT]** or **[FONT="Courier New"]http://host.domain.tld:80/directory/[/FONT]** or **[FONT="Courier New"]https://host.domain.tld/directory/[/FONT]** or **[FONT="Courier New"]http://host.domain.tld/directory/#[/FONT]** (or various combinations of those) result in a message saying that's not a valid format. Fail.
[*]At the DOS shell, **[FONT="Courier New"]net use ...[/FONT]** results in either System error 5 or System error 67 (might have been 69). Fail.
[*]Installing recommendations from Microsoft's Knowledge Base didn't fix anything either and probably munged the whole system.
[/LIST]

Anyone know of a link to a definitive solution from an authoritative source (as opposed to yet another "joe/jane q. random got it to work by dancing widdershins, naked under a full moon".)

---

