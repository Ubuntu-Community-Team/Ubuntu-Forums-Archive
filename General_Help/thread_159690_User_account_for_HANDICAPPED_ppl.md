---
title: "User account for HANDICAPPED ppl"
date: 2006-04-13
forum: General Help
---

### Post by ashrack on 2006-04-13
This LINUX os would have 2 user accounts, DIVJAK and BLUMEN. The DIVJAK account is already set up and will be used by ppl who are not handicaped.Now the account BLUMEN will be used by the handicaped ppl. And thus must contain the following:
1.resolution of 800x600 
2.must have accesibility features like GOK,GNOME-MAG,GNOPERNICUS set. 

Now how would I set it so account BLUMEN would have the same appereance, desktop icons, permissions,... as does the account DIVJAK??

---

### Post by mandrakethepenguin on 2006-04-13
While logged into user BLUMEN, type in a terminal```
sudo apt-get install gok gnome-mag gnopernicus 
```  Then you can configure the screen resolution in **System -> Prefrences -> Screen Resolution **and the handicapped prefrences in **System -> Prefrences -> Assistive Technology Support**.

---

### Post by ashrack on 2006-04-13
[QUOTE=mandrakethepenguin]While logged into user BLUMEN, type in a terminal```
sudo apt-get install gok gnome-mag gnopernicus 
```  Then you can configure the screen resolution in **System -> Prefrences -> Screen Resolution **and the handicapped prefrences in **System -> Prefrences -> Assistive Technology Support**.[/QUOTE]
that has already been done. But I still require the following:
> Now the account BLUMEN will be used by the handicaped ppl. And thus must contain the following:
1.resolution of 800x600 

Now how would I set it so account BLUMEN would have the same appereance, desktop icons, permissions,... as does the account DIVJAK??

---

### Post by ashrack on 2006-04-15
anyone?
>  Now the account BLUMEN will be used by the handicaped ppl. And thus must contain the following:
1.resolution of 800x600

Now how would I set it so account BLUMEN would have the same appereance, desktop icons, permissions,... as does the account DIVJAK??

---

### Post by Face1 on 2006-04-15
The only way I could see it having the same permissions is to have them as the member of the same group and set files with group permissions.  I know that doesn't really help, but that's the only thing I can think of.

As for having the same desktop, I believe you can set both user accounts to share one home directory (**System -> Administration -> Users and Groups**, right click on a user, click **Properties**, go to the **Advanced** tab, and set them to have the same home directory).  Within the home directory are the settings for desktop icons, etc--so they should be consistent over the two accounts. However, I'm sure this will cause permission issues, which I am not aware how to rectify.  Probably, the permissions of all the files in the home directory would have to be changed to allow group members the same privileges as users, and a new umask would have to be set, which would make it so new files would be created with permissions that allow groups the same privileges.  Unfortunately, someone more experienced than myself will need to explain how that is done -- as I don't really know.

Now, if the two users weren't sharing the same home directory, you could add lines in the /home/BLUMEN/.bashrc file to start those accessibility applications when you log on.  However, you can't do that, because both users will be executing the same .bashrc when they log on.  So, to accomplish this, we will need to use the environment variable **$USER**, which is always the username of the user currently logged on.  So the following lines could be added to the .bashrc file:
```

if [ $USER = "BLUMEN" ]
then
[INDENT]#code for starting accessibility applications goes here[/INDENT]
fi

```
Of course, you could also have commands specific to the other account executed in the same way.


[EDIT] Oops, I forgot about the screen resolution part of your question.  I'm not sure how that would be done, but there is probably some command that can be run to do it.  I just have no idea what it would be.

---

### Post by joelito on 2006-04-15
open /etc/X11/xorg.conf using nano or gedit with superuser settings(sudo)

Make sure there's a section that looks like this
```

Section "Screen"
	Identifier	"Default Screen" #ignore
	Device		"Intel Corporation Intel Default Card" #ignore
	Monitor		"Generic Monitor"  #Ignore
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

```

Then restart the Xserver and log in as blumen in synaptic

Go to system -> preferences ->screen resolution and select the resolution you want

Note that the parts marked with #ignore may be diferent for your configuration

---

### Post by ashrack on 2006-04-15
FACE1
tanx 4 your reply. But am afraid thats not exactly what I want. Should've been more specific in my questions, my bad, sorry.
What I want is that all of the DIVJAK's icons, appereance would just be copied to the BLUMEN account. But after that is done they would act like 2 seperates account. After reading MAN pages for USERADD I know that when creating a new account everything from "/etc/skel" is copied to it. But I saw no options on how to change the above mentioned directory???

---

### Post by Face1 on 2006-04-15
You may change the /etc/skel directory just as you would any other directory.  I'm not in front of my linux box right now, so I can't tell for sure, but you may need to use sudo commands when changing it, because of its permissions.

---

