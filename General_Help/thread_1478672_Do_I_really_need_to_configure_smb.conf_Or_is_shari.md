---
title: "Do I really need to configure smb.conf? Or is sharing folders enough?"
date: 2010-05-10
forum: General Help
---

### Post by Roasted on 2010-05-10
I've always used a GUI tool for customizing user shares with Samba. I have it set up with a total of 5 users.

Jason - me.
Curt - brother.
Tyler - brother.
Pam - mother.
User - Generic "Guest" account.

I have it set up so Jason can access everybody, but each user can only access their own share. AKA Curt can't access Tyler's stuff, etc.

Currently I would install system-config-samba and set up the shares there. Okay, fine. But do I "need" to do that? It seems as if I can just right click - share folder - and set the permissions accordingly. As long as I set Curt as the owner/group of "Curt" then Tyler gets denied access, etc.

So moral of the story is, what should I do? Is it still best or perhaps more robust to edit the smb.conf file accordingly? Or should I just install Samba and that's *IT* and don't bother editing the smb.conf anymore and just share folders out and set permissions accordingly?

---

### Post by dtfinch on 2010-05-10
I mostly use swat for configuring samba. It shows you all possible options in smb.conf, with links to documentation. It's easier than editing smb.conf directly, but without sacrificing any flexibility.

In addition to allowing each user access, you'll probably want to either "force user" to one user on the shares, or set create mask (and probably others I can't immediately remember) to loose enough permissions to let everyone access the files that others create in the share. Otherwise you can end up with an odd situation where each person can create files in a single share, but none of them can access each others' files.

There might be easier ways to do it now, but that's how I've always done it since 4-5 years ago.

---

### Post by Roasted on 2010-05-10
So using samba with the smb.conf is more convenient because you can do far more with it, such as forcing the mask as you mentioned.

Basically it's the same thing, it's just editing the smb.conf (or using a GUI tool for it) just offers more options.

Eh?

EDIT - The only thing is, forcing a mask isn't really necessary if you set the group user ID on the folder, which is what I do. That way all data that comes through gets those permissions/group assignment accordingly. I guess that just kind of takes care of that department, unless there's something I'm missing.

---

