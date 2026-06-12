---
title: "Copying files to Apache Server"
date: 2011-05-09
forum: General Help
---

### Post by gtmtnbiker98 on 2011-05-09
Here's my setup:

I have Ubuntu Server 11.04 freshly installed.  I have setup SAMBA to share out /var/www.  The SAMBA setup forces user root with a valid user name with write access.  This makes the SMB share visible on our Windows network.  I've used this setup in the past without issue.

I have recently updated our Web site using Dreamweaver on a Macbook Pro.  Copied the HTML files over to a Windows server share as a repository.  Whenever I attempt to copy over the new HTML files to the Web server (accessing SAMBA SHARE titled "Web Site) I get an error message from Windows stating "Are you sure you want to copy this folder without its properties."  When I click on "Yes" the files copy; however, some of my HTML documents cannot be found when clicking the appropriate hyperlink from a Web browser.  All of the documents are on the Web server, but I cannot for the life of me figure out what "Properties" are not being copied and why.

I have also tried copying the HTML files directly from the Macbook Pro to the SAMBA SHARE and I do not receive any permissions warning, I receive the same result as noted above.    

The Ubuntu 11.04 Apache box with the /var/www folder shared is writeable.  I have this same Web site running on a Mac OS X Snow Leopard development machine running Apache and it works just fine.  Any ideas?

I am chasing my tail with this one.

---

