---
title: "Copy existing user"
date: 2010-03-30
forum: General Help
---

### Post by Snoober on 2010-03-30
At first glance I didn't see this in the forums but it wouldn't surprise me if I missed it. Does anybody know the easiest way to copy/duplicate an existing user (theme, settings, etc.) if it's even possible? I know how to go to Users and then create a new user but often I'd like to use one as a template including the theme, power settings, etc.

Any help is appreciated. Thanks.

---

### Post by sisco311 on 2010-03-30
The /etc/skel directory contains files and directories that are automatically copied over to a new user's home directory when such user is created.

Make all the changes you want and copy the content (or the config files) of the user's home to /eetc/skel.

Or try sabayon, a GUI tool for user settings management.

---

### Post by Snoober on 2010-03-30
I think Sabayon is exactly what I was looking for. Thank you.

---

