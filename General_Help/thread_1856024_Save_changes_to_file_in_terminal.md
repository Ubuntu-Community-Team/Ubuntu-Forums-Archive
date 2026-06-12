---
title: "Save changes to file in terminal?"
date: 2011-10-07
forum: General Help
---

### Post by Mr.Enigma on 2011-10-07
Okay this question is actually for CentOS, but i'm assuming it's going to be the same as Ubuntu.

How do I save a file from the terminal?

EG:  from root it type visudo
I edit the visudo file to add sudo to the user I want.

then what?  How do i save my changes?  Why isn't this documented anywhere?  I've pushed ctrl + every button on my keyboard with no luck (well, excluding bad luck w/ ctrl+U)

---

### Post by haqking on 2011-10-07
> **Mr.Enigma said:**
> Okay this question is actually for CentOS, but i'm assuming it's going to be the same as Ubuntu.

How do I save a file from the terminal?

EG:  from root it type visudo
I edit the visudo file to add sudo to the user I want.

then what?  How do i save my changes?  Why isn't this documented anywhere?  I've pushed ctrl + every button on my keyboard with no luck (well, excluding bad luck w/ ctrl+U)

it is documented in thousands of places, however if you dont know how to use vi/vim then running it under sudo/root to edit the sudo file might not be the best decision ;-)

:w to save

---

### Post by CharlesA on 2011-10-07
Nano would work too, but when using vi or vim, :wq writes the file, then quits. :)

A quick google found this guide: [http://www.linuxhelp.net/guides/vim/](http://www.linuxhelp.net/guides/vim/)

---

### Post by sisco311 on 2011-10-07
It depends on how visudo was compiled, but usually you can use the EDITOR and VISUDO environment variables to specify the editor you want to use. As root:
```
EDITOR=nano visudo
```
or
```
VISUDO=gedit visudo
```

---

### Post by Mr.Enigma on 2011-10-07
@sisco311
Thank you, I think that will be easier than trying to learn how to save.

@haqking / CharlesA
Thank you, but i really don't know what ":w" means. I can't just type it in because then it just types it into the file.

I understand where your coming from about not editing it with root, but that's the only way available to me as no other user has the ability to edit it.  Which is why I'm adding sudo privileges in the first place.

---

### Post by CharlesA on 2011-10-07
Does it say "INSERT" at the bottom of the screen?

If so - hit escape and then type :w and hit enter.

---

### Post by WasMeHere on 2011-10-07
To change privileges (including administration) you can also use a menu. In the traditional interface of  Ubuntu, gnome it is
*System -- Administration -- Users and Groups*

Select *user* and change *Account type* or enter *Advanced settings*

I don't know but guess there is a similar menu in CentOS.
     -o-
In terminal I use **gedit** to edit regular files (as a user),
and I use **sudo nano** to edit system files (as root (superuser)). 

gedit and nano are more similar to editors of the windows world than vi(m). I would not say more intuitive, it is just a matter of what you are used to.

---

### Post by haqking on 2011-10-07
> **Mr.Enigma said:**
> @sisco311
Thank you, I think that will be easier than trying to learn how to save.

@haqking / CharlesA
Thank you, but i really don't know what ":w" means. I can't just type it in because then it just types it into the file.

I understand where your coming from about not editing it with root, but that's the only way available to me as no other user has the ability to edit it.  Which is why I'm adding sudo privileges in the first place.

in vi/vim you enter text in insert mode by pressing i.

when you want to save you press esc then : (colon) which escapes the insert mode then you type w to save, or wq to save and quit

if you are going to use vi/vim run vimtutor from the command line to learn how to use it, otherwise use as others have suggested.

---

### Post by Mr.Enigma on 2011-10-07
@CharlesA
That was my problem.  Thank you

the visudo=gedit visudo command failed miserably. It still opened it in the terminal instead of launching gedit

Edit: it's worth pointing out that I had no idea i was using a app called vim, I was searching for "save a file using terminal" which provided results useless to my situation.

---

