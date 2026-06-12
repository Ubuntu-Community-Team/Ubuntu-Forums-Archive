---
title: "Spotify playlist links"
date: 2010-01-08
forum: General Help
---

### Post by blazemore on 2010-01-08
Is there a way to share links to Spotify playlists with users who are running it through Wine?
Obviously clicking a spotify: link doesn't work (Unless the browser is running in Wine)

---

### Post by blazemore on 2010-01-11
Bumped after 2 days :-)
Sorry!

---

### Post by ionte on 2010-01-12
You can paste the link into the search field of spotify.

---

### Post by kostkon on 2010-01-12
> **blazemore said:**
> (Unless the browser is running in Wine)
No, it's not needed. You just need to create a script and setup your browser. The instructions are [here on the Spotify site (under the section *Opening spotify URIs from browsers*]("http://www.spotify.com/en/help/faq/wine/")).

The only thing is that you'll need to change the line:
```
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$@"' >> ~/.browser2spotify
```
to
```
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$1"' >> ~/.browser2spotify

```
My own version of the script is this:
```
#!/bin/sh

cd "/home/xxxxx/.wine/drive_c/Program Files/Spotify";
wine "spotify.exe" /uri "$1";
```

Hope that helps.

---

### Post by ron999 on 2010-02-28
Hi
Please can somebody explain how to share my own Spotify playlists.
When I right-click 'Copy HTTP Link' or 'Copy Spotify URL' nothing gets copied.

---

### Post by ron999 on 2010-03-08
Bump

---

