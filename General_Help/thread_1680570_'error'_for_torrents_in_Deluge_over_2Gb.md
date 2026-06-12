---
title: "'error' for torrents in Deluge over 2Gb"
date: 2011-02-02
forum: General Help
---

### Post by jarthurs on 2011-02-02
I've just setup a virtual Ubuntu 10.10 machine on my server running Deluge and WebUI. The WebUI seems to work fine, but if I upload a torrent with a total size over 2Gb I just get an 'error' as soon as the torrent is run.

The download folder is a CIFS share to a NAS (Acer Altos EasyStore) folder, I can download torrents that are less than 2Gb in total without any problems. 

The share is mounted in fstab:

//nas/media/torrents /mnt/nas cifs credentials=/home/jason/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 

I can read/write large files from the command line or Nautilus but any torrent uploaded to Deluge larger than 2Gb is flagged as 'error' as soon as it is run (with no actual error listed in the torrent details).

Regards,
Jason.

---

### Post by jarthurs on 2011-02-03
> **jarthurs said:**
> I've just setup a virtual Ubuntu 10.10 machine on my server running Deluge and WebUI. The WebUI seems to work fine, but if I upload a torrent with a total size over 2Gb I just get an 'error' as soon as the torrent is run.

The download folder is a CIFS share to a NAS (Acer Altos EasyStore) folder, I can download torrents that are less than 2Gb in total without any problems. 

The share is mounted in fstab:

//nas/media/torrents /mnt/nas cifs credentials=/home/jason/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 

I can read/write large files from the command line or Nautilus but any torrent uploaded to Deluge larger than 2Gb is flagged as 'error' as soon as it is run (with no actual error listed in the torrent details).

Regards,
Jason.

It appears that adding the 'nounix' attribute to the mount in /etc/fstab allows the NAS to happily accept torrents larger than 2Gb. It's a solution, but I still have no idea what the problem was...

Regards,
Jason.

---

