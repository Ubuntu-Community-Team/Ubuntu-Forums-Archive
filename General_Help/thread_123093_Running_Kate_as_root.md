---
title: "Running Kate as root"
date: 2006-01-29
forum: General Help
---

### Post by Olflo on 2006-01-29
Hi,
I would like to run Kate as root, using sudo kate, in order to edit system files.
Doing so returns:

Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

So I guess, Kate is trying to read "/var/tmp/kdecache-olflo" instead of  "/var/tmp/kdecache-root". But why? And what can I do?

---

### Post by GeneralZod on 2006-01-29
I always use kwrite instead; it works with sudo, and is lighter.

---

### Post by Alpha_toxic on 2006-01-29
I also ran into that, so I just installed Kwrite. I'd like to fix Kate though. It's a much more powerfull editor.

---

### Post by Olflo on 2006-01-29
Yes,
indeed I have installed kedit meanwhile to work around.
But I like the integrated Interface of Kate: having an editor, filesystem browser and shell in one window is nice. So why start another application if you want to edit something as root? thats so incoherent...

---

### Post by GeneralZod on 2006-01-29
[QUOTE=Olflo]Yes,
indeed I have installed kedit meanwhile to work around.
But I like the integrated Interface of Kate: having an editor, filesystem browser and shell in one window is nice. So why start another application if you want to edit something as root? thats so incoherent...[/QUOTE]

It's a bug, not a feature :)

Anyway, you can do 

```

kdesu kate

```

as a workaround if you really want to, but then you have to enter your password every time.

---

### Post by noigeaR on 2006-02-01
if you use **konqueror** you can easily edit files in root mode with kate.

right click the file you wish to edit -> actions -> edit as root

enter your password and you can edit the file with root privileges.

---

### Post by Lord Illidan on 2006-02-01
sudo kate works for me. It gives the 2 warnings described but then loads no probs. Is it because i have KDE 3.5 installed?

---

### Post by Neo Ex on 2006-02-01
It happens to me, too (in fact I use 'kdesu kate'), but I'm nearly sure it also happened with KDE 3.4.x.

---

