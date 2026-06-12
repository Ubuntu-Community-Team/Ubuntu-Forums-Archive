---
title: "Shared samba printer is really slow"
date: 2006-06-13
forum: General Help
---

### Post by bohboh on 2006-06-13
I have my canon ip4000 connected up using cups and turborprint drivers. This works fine and prints instantly.

I have it shared and connected on my winxp laptop. Getting it to connect took a while, it found the printer ok. but installing drivers took about 5 minutes. And everything about it is really slow. Printing, opening the properties window, carrying a test print. Printing itself take ages, a one line text file takes about 3 minutes to print.

I am using the latest samba, turboprint and cups software.

What can i do to speed it up?

---

### Post by bohboh on 2006-06-14
Managed to speed it up by deleting some registry entries in XP. Not as fast as it would be if it was XP to XP, but quick enough.

FYI [http://www.edoceo.com/liber/gentoo-samba-cups.php]("http://www.edoceo.com/liber/gentoo-samba-cups.php")

---

### Post by mssever on 2006-07-07
> **bohboh said:**
> Managed to speed it up by deleting some registry entries in XP. Not as fast as it would be if it was XP to XP, but quick enough.

FYI [http://www.edoceo.com/liber/gentoo-samba-cups.php]("http://www.edoceo.com/liber/gentoo-samba-cups.php")

Thanks a bunch. I had a similar problem. I'm posting the registry keys that I had to delete, because they were a little different from that link (and because most of the document is irrelevant to the situation at hand).

I deleted [FONT="Courier New"]HKEY_CURRENT_USER\Printers[/FONT] and all subkeys.

[COLOR="Gray"]Oddly enough, I have no idea what is happening with this bug, because the slowdown is due to megabytes (someimes even gigabytes) of data being transferred between the two machines.[/COLOR]

---

