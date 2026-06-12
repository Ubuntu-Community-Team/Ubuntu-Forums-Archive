---
title: "Web Setup - SFTP Access"
date: 2011-03-15
forum: General Help
---

### Post by chistophe on 2011-03-15
hi Ubuntu community, 

I'm a noob here so I'm hoping someone can point me in the right direction. My question is around "best practice" for setting up web access via SFTP for contract developers/agencies (On Ubuntu Server / Apache)

To summarize, we use various agencies depending on the site content we are building and I would like to give these users access to drop/modify files. All the sites are set up virtual host style, living under /var/www/ but I guess I'm not really sure to go from there? If I set them up to have home directories in the /~user/public_html format, then that doesn't really make sense if ownership or the contract changes down the road. Is there a way that I should be setting the user up to drop files in their home directory, but those files are really linked to /var/www/sitename? 

I think a best practice piece on web set up with 3rd party development is what I am looking to get some more detail on. Any help is greatly appreciated! 

Thanks, 
Chris

---

