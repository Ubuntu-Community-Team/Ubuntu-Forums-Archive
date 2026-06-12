---
title: "Granting Wordpress permission to wp-content"
date: 2010-03-07
forum: General Help
---

### Post by Mike Bird on 2010-03-07
I recently moved from Windows to Ubuntu 9.10, and I'm learning more about Ubuntu every day. Today, I'm attempting to install Wordpress using my computer as the host. Everything has either been successful or problem-solved to this point. However, Wordpress requires permission to edit wp-content (e.g. to modify themes), but I don't know how to grant permissions. I changed the permissions for the www-data group through gksudo nautilus. I don't know if www-data is the correct access group. I also added myself to the www-data group, but I'm doubtful that I did it correctly. I feel that I don't understand how permission groups work. Likewise, I don't know how to access var/www/ through the terminal to try chmod commands (I've read about '775' permission on the WP Codex). 

Sorry for the lack of detail. I would be happy to try and provide further details to your questions. My searches of both this forum and in general have yielded results that either don't apply or are unclear. If you could provide a brief description of how to implement a solution, it would be especially helpful. I appreciate any clarification or assistance. Thank you for your time.

Edit: My current solution is to grant access to everyone for the wp-content folder. It feels like a temporary solution, but it's working nonetheless.

---

