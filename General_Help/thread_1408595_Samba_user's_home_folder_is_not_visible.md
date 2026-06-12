---
title: "Samba user's home folder is not visible"
date: 2010-02-16
forum: General Help
---

### Post by aguzman on 2010-02-16
Hi,

I'm having some trouble with the user's home folders in Samba, ubuntu clients.

I have a Samba server (Ubuntu Server 9.10) and a bunch of windows clients and ubuntu clients too.

On windows clients, each user, can see his home folder without problems, and the other shared folders too of course.

The problem appears in ubuntu (i'm  using gnome desktop with nautilus and the plugin for samba). When I enter Places->Network->Windows Network->DOMAIN->SERVER I only see the public shared folders, but no the samba user's home folder.

I tryied connecting to samba through Places->Connect to Server and entering the username (for previous auth just in case) but nothing happens...

If, in nautilus I write smb://server/username, once it asked me for my user and password (but I told the popup to keep the password forever so now it doesnt ask me anymore :S), but it keeps not showing the folder under SERVER, the only way to access it is through smb://server/username directly. Even username@server does not work.

Mi auth type in the Samba server is "user", and the auth config at my ubuntu client is also user.

Just in case.. when I type smbclient -L //SERVER -U username, it shows me the home folder ok.

Am I missing something? or I'll have to share explicitly share each home folder leaving them visible to all users?

Thanks!

---

### Post by crazybert123 on 2010-09-01
Same issue

Both client and server have Ubuntu 10.04.1
Windiws7 shows home share just fine.

Any updates?

---

