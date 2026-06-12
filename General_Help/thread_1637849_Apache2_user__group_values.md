---
title: "Apache2 user / group values"
date: 2010-12-05
forum: General Help
---

### Post by prickly on 2010-12-05
I am following (Debian) documentation for installing VIMP on Lucid. I have reached a point where I need to configure the following values for Ubuntu but have had no luck finding the settings that I need. 

The values below are the Debian user and groups values for Apache2. 

How or where do I find out what the Ubuntu equivalents are? 


```
server_user: 
type: string 
value: www-data 
name: 'Server Benutzer' 
description: '' 
editable: false 
system: false 
nullable: false 
server_group: 
type: string 
value: www-data 
name: 'Server Gruppe' 
description: '' 
editable: false 
system: false 
nullable: false
```

The command that will not run is:

```
./symfony framework:init mysql://showvid:<password>@localhost/showvid
```

The documentation states:

The framework:init task sets owner and group for all files to www-data and www-data, which is default for Apache2 and Debian. If you are installing ViMP under a different Linux distribution, please check the "Changing username and password" section in the Appendix. [See the values above].

Any help with this is greatly appreciated as this is close to the final step of the installation!

---

### Post by cavalier911 on 2010-12-05
Upload the english ViMP 2.0 Installation Guide.pdf your refering to as an attachment in your reply

---

### Post by prickly on 2010-12-05
> **cavalier911 said:**
> Upload the english ViMP 2.0 Installation Guide.pdf your refering to as an attachment in your reply

The guide is too big to upload as an attachment here so I have temporarily uploaded it elsewhere: [http://pricklytech.files.wordpress.com/2010/12/installation_guide.pdf](http://pricklytech.files.wordpress.com/2010/12/installation_guide.pdf)

Thanks for taking a look at this for me! :D

---

### Post by prickly on 2010-12-07
I have managed to progress further now - Sourceguardian is required for the community version.

Now I just need to fix the mixmatch of sourceguardian versions between the one supplied in the application and the ones that are available for download - hopefully this will fix the error message ...

---

