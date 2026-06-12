---
title: "Strange problem with tangerine-icon-theme"
date: 2006-05-03
forum: General Help
---

### Post by Circleback on 2006-05-03
I get some strange messages when i try to install anything regarding the tangerine icon theme. Ive tried aptitude and apt fix broken install and get this message

Preparing to replace tangerine-icon-theme 0.10-0ubuntu1 (using .../tangerine-icon-theme_0.10-0ubuntu1_all.deb) ...
Unpacking replacement tangerine-icon-theme ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

any ideas on how to fix this would be great as i cannot install anything new until this is fixed

---

