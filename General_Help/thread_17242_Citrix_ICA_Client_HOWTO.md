---
title: "Citrix ICA Client HOWTO"
date: 2005-02-27
forum: General Help
---

### Post by psypher on 2005-02-27
Hello. I struggled a bit installing the Citrix client so I'm posting this for everyone else just in case:

1. Download ica client: linuxx86.tar.gz
2. sudo apt-get install libxaw6 (i have the uni, multiverse and marrilat stable repositories enabled)
3. run setupwfc from uncompressed citrix folder (note uncompress tar.gz to a folder without spaces and run install as root or sudo ./setupwfc)
4. Install client with all defaults 

Done!
That worked for me!

---

### Post by us3rQUE on 2005-03-03
Does anyone know how to configure the "Rdesktop client"(Terminal Server Client) to locate 'wfica'?? :confused:

---

### Post by gsaito on 2005-07-22
I'm also looking for help on this. When I try to use Terminal Server Client to connect to a Citrix (ICA) server, it reports the error:

"Failed to execute the following process: "wfica" (no such file or directory)"

However, I know that ICA client is installed on /usr/lib/ICAclient

Any leads? :neutral:

---

### Post by Ruskie on 2005-07-29
[QUOTE=gsaito]I'm also looking for help on this. When I try to use Terminal Server Client to connect to a Citrix (ICA) server, it reports the error:

"Failed to execute the following process: "wfica" (no such file or directory)"

However, I know that ICA client is installed on /usr/lib/ICAclient

Any leads? :neutral:[/QUOTE]
 Try putting that on path: wfica is the executable, and should be there in the directory you mentioned.
Also check the permissions of the file.

---

