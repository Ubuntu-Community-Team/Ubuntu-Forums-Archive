---
title: "Web development - local dns redirection?"
date: 2011-06-21
forum: General Help
---

### Post by PaulWhipp on 2011-06-21
I develop websites on my Ubuntu (10.04 LTS) powered workstation which runs a desktop development environment and a local webserver (Apache 2, MySQL etc.)

Most of the time I can access my development sites fine by a url such as "HTTP://dev/<clientsitefolder>" and all is fine.

Unfortunately some CMS and ecommerce applications store the site URL in either configuration files, the database or both. Examples of this are Magento and Joomla. They also use URL rewrites and the like.

I would really like to be able to redirect the full and correct URL (e.g. [www.example.com](www.example.com) to the local folder while working on it). Sure it gives me enough rope but it means that I will no longer have to muck around with local configuration files and special database scripts and the like.

The ideal would be for me to be able to switch from the local mapping to the real mapping at will and for the mapping to work from my virtual box emulations too (they run all sorts of different browsers for testing purposes).

Can someone point me to the relevant code/documentation or something to allow me to do this?

---

