---
title: "Upload manager program"
date: 2010-04-27
forum: General Help
---

### Post by alexlittle on 2010-04-27
Hi,

I'm looking for an equivalent of a download manager, but for uploads (so that the upload of large files can be stop/started at will, or if there is a connection problem).

Essentially I have a Ubuntu server in Ethiopia which I'd need to transfer large(ish) files to (up to around 100Mb), most likely from a Ubuntu desktop. The internet connection to this server can be very erratic and uploading large files (via ftp or scp) more often than not fails.

I realise that I'd need some program on the server to accept the incoming file. I'm not sure if FTP supports this type of transfer?

Hope that makes sense and that I've posted in the correct forum area (feel free to move if not). Any help/advice much appreciated.

Cheers,
Alex

---

### Post by switch10 on 2010-04-27
You could use rsync with the -u option.  This way, if you needed to stop it, it could be resumed easily..

---

