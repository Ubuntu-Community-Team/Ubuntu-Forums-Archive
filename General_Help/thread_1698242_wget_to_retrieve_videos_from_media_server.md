---
title: "wget to retrieve videos from media server"
date: 2011-03-02
forum: General Help
---

### Post by rohitratri on 2011-03-02
Hi, 
I'm trying to collect media from a media test server in an effort to collect some test data (videos). 
The structure of the site is thus -
1. Once logged in with a user name and password user is presented with "home page".
Home page lists directories (different formats) -
2. On clicking on a directory link, it shows a page with videos listed in it.
3. On clicking on video link, it opens a video page which in turn has a "download" to dwld the video.
 
I'm using the following command and I only the home page and it would not recurse further at all :confused: -
 
wget -r -l10 -np -p -H -U "Mozilla" -e robots=no -A.mp4,.mpeg,.3gp,.avi --user=xxx --pass=xxx --wait=5 "URL"
 
 
Any idea what could be going wrong?
 
Thanks
Rohit

---

