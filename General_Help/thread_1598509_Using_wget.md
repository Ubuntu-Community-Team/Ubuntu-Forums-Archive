---
title: "Using wget"
date: 2010-10-16
forum: General Help
---

### Post by Daimonan on 2010-10-16
Hi all,

This is probably a simple question, but I'll ask it anyway, as I haven't been able to find the answer online.

I'd like to use wget to download a file off of my school's CMS.  Its behind a 'password wall', but I do have the address of the file itself.  When I use wget to try and access the file, I instead get the HTML page corresponding to login page.

Is there a way to provide this information to the authentication (https) server so it thinks I already have a session and will thus give me the file I really want?

Also, I realize there are easier ways to do this, but I'm often working on a windows computer through Putty, and I'd like to be able to get files like this on the command line.

The URL of the file is:
[https://connex.csc.uvic.ca/access/content/group/76c2abfc-f107-4e0e-ac1b-86959a2087d1/linkLab.tar](https://connex.csc.uvic.ca/access/content/group/76c2abfc-f107-4e0e-ac1b-86959a2087d1/linkLab.tar)

You'll see the password wall if you try that link.

Thanks,

-David

---

### Post by CharlesA on 2010-10-16
As far as I know you can't use wget to access files in password protected areas.

---

### Post by junapp on 2010-10-16
from:[http://stackoverflow.com/questions/1324421/wget-post-data-hwto](http://stackoverflow.com/questions/1324421/wget-post-data-hwto)

might work for you. I modified slightly.

# Log in to the server.  This can be done only once.                   
wget --save-cookies cookies.txt \
     --post-data 'eid=foo&pw=bar' \
     [https://connex.csc.uvic.ca/access/login](https://connex.csc.uvic.ca/access/login)

# Now grab the page or pages we care about.
wget --load-cookies cookies.txt \
     -p [https://connex.csc.uvic.ca/access/content/group/76c2abfc-f107-4e0e-ac1b-86959a2087d1/linkLab.tar](https://connex.csc.uvic.ca/access/content/group/76c2abfc-f107-4e0e-ac1b-86959a2087d1/linkLab.tar)

---

