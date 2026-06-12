---
title: "lftp need help"
date: 2011-10-29
forum: General Help
---

### Post by mybrain87 on 2011-10-29
I'd like lftp to be able to do the following 4 things:

1. all files from all the folders and subfolders on the remote server should be downloaded into one single folder on the local. So that everything from those remote folders is just in one folder on the local machine.

2. exclude all files with the extension .nfo from beeing downloaded.

3. it should download the newest files first.

4. i'd like lftp to remember which files it downloaded successfully, even after they are gone from the download directory, so that it doesn't download those files into the download directory again.

Are those things possible?

Help is very appreciated.

---

### Post by mybrain87 on 2011-10-30
Okay  the last 3 parts i managed to do myself.

for 2 I specified a size-range and so those nasty nfo files won't be downloaded.

3 and 4 I bypassed by generating a lastfile which takes the timestamp from the last downloaded file and telling lftp to download only files newer-than that lastfile. So im getting only the new stuff even if the old ones are gone from the download directory.  --> Not tested yet. Hope it will work

For 1 I could still need some help, if what I want there is even possible.

---

