---
title: "FastCGI and APC Cache"
date: 2011-09-19
forum: General Help
---

### Post by windwardquay on 2011-09-19
I have a 10.04LTS dedicated server with currently 5 Joomla sites and 1 Magento in Apache virtual hosts. At the moment it is all in dev mode before we move our 

I need to use APC Cache for the connection between Joomla and Magento. APC and PHP are global.

Should I use FastCGI? What would be the benefits?

Another problem that concerns me is that there could be cnflicts between sites in the cache and I need to protect against this. Should I simply use apc.file_md5 and apc.canonicalize to separate things or do I really have to use locals calls?

If so can anyone recommend some implementations to follow?

---

