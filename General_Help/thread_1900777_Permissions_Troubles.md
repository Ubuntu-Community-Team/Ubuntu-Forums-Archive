---
title: "Permissions Troubles"
date: 2011-12-27
forum: General Help
---

### Post by c3ntury on 2011-12-27
I recently tried to lock a secondary user down to their own home directory using the command 'chmod 700 /home -R'. However, this has completely buggered up my entire permissions.

On my web server (apache2), I have a folder, say, 'downloaded'. It cannot be viewed (as a list of directorys) from a web browser unless the owner of the folder (recursively) is 'www-data'. However, unless the owner of the folder is 'rtorrent', the folder cannot be written to.

My web root is /var/rutorrent/, and there is a symlink to /home/rtorrent/downloaded/ in /var/rutorrent/ named 'downloads', which is the folder I'm talking about.

The result is that I can either view the folder from the outside world, or download files to it - but not both.

Does anyone know any way to reverse this travesty I seem to have caused? Or at least, how to fix this annoying problem?

Thanks and regards,
Cameron.

---

