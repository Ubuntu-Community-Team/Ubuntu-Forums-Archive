---
title: "Per-user web directories"
date: 2009-10-26
forum: General Help
---

### Post by Stawl on 2009-10-26
I have tried to do the tutorial on the apache page, and other pages, but haven't made much progress. Currently i have the httpd working but when i try to access the pages via another browser it won't show. It will give me the error 403 Permission denied. And besides that, the file httpd.conf has already UserDir enabled. Im clueless ^^ any help?

---

### Post by OpenGuard on 2009-10-26
```
sudo a2enmod userdir

```Add to your httpd.conf file:
```
<IfModule mod_userdir.c>
    UserDir Public
</IfModule>
``````
mkdir $HOME/Public
```Now, create a test file under Public directory and see how it turns out ..

```
http://127.0.0.1/~username
```

---

### Post by Stawl on 2009-10-27
> **OpenGuard said:**
> ```
sudo a2enmod userdir

```Add to your httpd.conf file:
```
<IfModule mod_userdir.c>
    UserDir Public
</IfModule>
``````
mkdir $HOME/Public
```Now, create a test file under Public directory and see how it turns out ..

```
http://127.0.0.1/~username
```

ok thanks, i but i have another problem... in the ubuntu server it worked, in the whitebox (another linux distro) the first line, a2enmod userdir says command not found, any idea? :s

EDIT: NVM IT'S WORKING ON BOTH! Thanks :) the problem was another thing >.> (forgot to restart the httpd service)

---

