---
title: "Getting tired of asking for file permissions"
date: 2009-10-09
forum: General Help
---

### Post by Kasinator009 on 2009-10-09
All I want to do is add a new theme to my cairo dock. But ubuntu just keeps its door locked on me demanding file permissions. Is it possible to maintain superuser file permissions as soon as I log in (  ](*,) it feel a lo like this right now)? if not can someone please help me through this troublesome process I am going through?

---

### Post by andy16666 on 2009-10-09
Can you explain the steps you are taking that are causing it to ask for permissions?

---

### Post by Kasinator009 on 2009-10-09
I am trying to drag a new cairo dock theme in to the theme folder thats it.

---

### Post by Kasinator009 on 2009-10-09
any way i can just enable permissions 24/7?:confused:

---

### Post by lovinglinux on 2009-10-09
> **Kasinator009 said:**
> I am trying to drag a new cairo dock theme in to the theme folder thats it.

Cairo dock themes are placed in your home directory, so you should have permission to save there without using sudo. Check the permissions of your home folder and the Cairo folder.

About how to gain superuser rights at login, this is not allowed to be posted in the forums, due to security reasons. You shouldn't do that and there aren't any good reasons to do so.

---

### Post by Kasinator009 on 2009-10-09
i really dont understand why to prevent kernal tampering? I mean isnt that like what open source is all about? oh well well it wasnt in the home directory. it was in my file system under user share cairo-dock themes.

---

### Post by ad_267 on 2009-10-09
I don't use Cairo dock, but the way themes and settings are stored in many Linux applications is that there are system wide settings and user settings. If you're installing new themes you should install them in your home directory. For normal use you should never need to do anything with files outside of your home directory.

It's not to prevent kernel tampering (whatever that might be), it's for security purposes. This prevents any application from having complete access to your whole system.

---

### Post by jeremyswalker on 2009-10-09
You shouldn't be copying the theme to the filesystem, unless you intend it to be a system wide theme for all users to use. It should just need copied into a directory in your home folder. Such as: /home/<username>/.cairo-dock/themes/
Something along those lines, anyway.

---

### Post by Boondoklife on 2009-10-09
If you are really wanting to move it to that location, why not just use `gksudo nautilus` and move it in that window?

---

### Post by Kasinator009 on 2009-10-09
ytea didnt work
 I know it HAS to go in the themes folder. but i cant enable folder permissions.

---

### Post by wdzieczny on 2009-10-09
have you granted the file permissions for your user? try 'chown 777' or gksu and just checking the permissions off.

---

### Post by ad_267 on 2009-10-09
> **Kasinator009 said:**
> ytea didnt work
 I know it HAS to go in the themes folder. but i cant enable folder permissions.

No it doesn't!

Depending on your version of Cairo it will either go in /home/USER_NAME/.config/cairo-dock/themes or in /home/USER_NAME/.cairo-dock/themes

It only has to go in /usr/share/cairo-dock/themes if you want the theme to be available for all users.

---

### Post by Kasinator009 on 2009-10-09
gksu opens but how do i enable permissions from there?

---

### Post by Kasinator009 on 2009-10-10
last call for tonight please pm me if this goes away

---

### Post by Vaphell on 2009-10-10
if you do gksu nautilus from terminal you have a file browser with admin rights - it means that you can freely move stuff around. But elevate your privileges only when you absolutely have to - accidental shift-delete or misclicked drag and drop in the wrong place and your system is destroyed. Kill that privileged window as soon as you finish your task.

if you know the exact position of that target dir you can copy stuff from command line:
sudo cp -r /source/path/with/goodies /usr/share/wherever/it/should/go

sudo will ask for pw and copying will be performed with admin rights.

but i agree with people that stuff like skins doesn't have to be applied system wide, proper place in the home directory should be enough.

---

### Post by Kasinator009 on 2009-10-10
Thanks it worked! Is there anyway to make nautilus my default file browser? I'm still fine tuning Linux here.

---

### Post by DeMus on 2009-10-10
> **Kasinator009 said:**
> All I want to do is add a new theme to my cairo dock. But ubuntu just keeps its door locked on me demanding file permissions. Is it possible to maintain superuser file permissions as soon as I log in (  ](*,) it feel a lo like this right now)? if not can someone please help me through this troublesome process I am going through?

This is the whole concept of Linux: Safety first.
You are logged in as a regular user with limited privileges. You can use the computer, use the installed programs and that's it.
When you want more: install programs, drivers, etc, you need to become root with more privileges. This is an unsafe situation. One mistake can destroy your whole system and that is not what you want. So you have to be root as little as possible.
Logging in as root is a big NO in the Linux world. It's the standard way in Windows and that's just the reason why a Windows system is so unsafe.
Do yourself a gigantic favor and remain the normal user Linux wants you to be instead of doing things as root. I know there are times you need to become root for a moment and that's okay, but only for a moment.

---

### Post by jeremyswalker on 2009-10-10
> **Kasinator009 said:**
> Thanks it worked! Is there anyway to make nautilus my default file browser? I'm still fine tuning Linux here.

If you are using Ubuntu, Nautilus is your default file browser. If you are looking to make root privileges in Nautilus default, I highly recommend against such action.

---

### Post by oldos2er on 2009-10-10
> **Kasinator009 said:**
> Thanks it worked! Is there anyway to make nautilus my default file browser? I'm still fine tuning Linux here.

 If you're using Gnome, Nautilus should already be your default file manager. If you could explain a little more about what exactly you want to do, it would help.

---

### Post by Kasinator009 on 2009-10-10
my apologies I am using gnome as well as dolphin as my file manager. I herd dolphin was good so i used it right off the bat. Am I wrong? does it stink?

---

### Post by jeremyswalker on 2009-10-10
> **Kasinator009 said:**
> my apologies I am using gnome as well as dolphin as my file manager. I herd dolphin was good so i used it right off the bat. Am I wrong? does it stink?

Personal opinion... Yeah, dolphin stinks. I think you should stick with Nautilus. If you were going to use a file manager from kde, it should have been konqueror. IMHO

What steps did you take to make dolphin your default file manager??

---

### Post by SuperSonic4 on 2009-10-10
> **Kasinator009 said:**
> my apologies I am using gnome as well as dolphin as my file manager. I herd dolphin was good so i used it right off the bat. Am I wrong? does it stink?

In my opinion Dolphin is the best file manager but I still wouldn't use it on a gnome desktop (I use KDE where it's default).

---

### Post by jeremyswalker on 2009-10-10
> **SuperSonic4 said:**
> ...but I still wouldn't use it on a gnome desktop (I use KDE where it's default).

I strongly agree with you here. If you are going to run a full featured desktop environment (like gnome or kde), it makes no sense to use a non default file manager. The file manager is arguably what the desktop environment is centered around. I would say, if you want to use dolphin, use kde. Otherwise, stick with Nautilus.

---

### Post by Kasinator009 on 2009-10-10
ok im back to nautilus thanks again everyone!

---

