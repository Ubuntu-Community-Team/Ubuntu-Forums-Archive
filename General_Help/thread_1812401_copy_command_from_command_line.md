---
title: "copy command from command line"
date: 2011-07-26
forum: General Help
---

### Post by helloise on 2011-07-26
can some body please just show me how to do this? i cant get it right

i want to copy files and direcories and make the directories if it does not exist

i tried:

a12:/home/rainbowcode/rainbowcode_deploy_versions/0.4.1.4#cp -R plugins/smartRouterPlugin/lib/form/SmartRouterConfigOptionsTableForm.class.php  home/rainbowcode/rainbowcode_deploy_versions/0.4.1.6/plugins/

the "smartRouterPlugin/lib/form/" path does not exist in 0.4.1.6
so it must copy the file and create the directories as it goes

for the life of me i cant get it right??
please help
thanks

---

### Post by Azdour on 2011-07-26
Hi,

At a quick glance it looks like you are missing the forward slash before 'home'. I think your cp should look like this:

```
cp -R plugins/smartRouterPlugin/lib/form/SmartRouterConfigOptionsTableForm.class.php /home/rainbowcode/rainbowcode_deploy_versions/0.4.1.6/plugins/
```

---

### Post by blind2314 on 2011-07-26
Please re-format your post using [code] tags around the command you're running and any output. That'll make it much easier to help.

---

### Post by helloise on 2011-07-26
i have the "/" but still not creating the smartRouterPlugin/lib/form directory path within the plugins directory

```

a12:/home/rainbowcode/rainbowcode_deploy_versions/0.4.1.4/plugins# cp -R smartRouterPlugin/lib/form/SmartRouterConfigOptionsTableForm.class.php /home/rainbowcode/rainbowcode_deploy_versions/0.4.1.6/plugins/


```

---

### Post by helloise on 2011-07-26
Yikes me very stupid...got it now

---

