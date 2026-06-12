---
title: "sending large files"
date: 2012-04-17
forum: General Help
---

### Post by psykatog on 2012-04-17
Just wondering - if I want to send a 6gb file to ONE person, would I be able to do so by creating a torrent file and giving that person the torrent?  I would not like it to appear on any public sites like Tpb or isohunt.

---

### Post by Ceiber Boy on 2012-04-17
> **psykatog said:**
> Just wondering - if I want to send a 6gb file to ONE person, would I be able to do so by creating a torrent file and giving that person the torrent?  I would not like it to appear on any public sites like Tpb or isohunt.
That sounds complicated! - if you have the cooperation of the person you wish to send the file to you could do an SSH connection between the two machines and SCP it across

Their are loads of tutorials on how to do this, if you need help ask and I'll or some one else I'm sure will be able to explain how to do this.

---

### Post by SeijiSensei on 2012-04-17
You'd need to run a "tracker" as well.  As Ceiber Boy says, use SCP or SFTP, or put the file on an 8GB USB key and mail it to the other person.

---

### Post by texpat on 2012-04-17
I'm not sure if this is correct, but the idea behind torrents is that you simultaneously download chunks of a file from different sources. That's what makes them so efficient, because you don't bog down a single server and take advantage of more bandwidth. If you have the file on a single server, doesn't that defeat the whole concept?

What if you split the file into smaller chunks and just e-mail these?

This may help:
[http://www.omgubuntu.co.uk/2010/08/split-large-files-easily-in-ubuntu-with-gnome-split/]("http://www.omgubuntu.co.uk/2010/08/split-large-files-easily-in-ubuntu-with-gnome-split/")

---

