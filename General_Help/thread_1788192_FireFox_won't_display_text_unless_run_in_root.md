---
title: "FireFox won't display text unless run in root"
date: 2011-06-22
forum: General Help
---

### Post by c0stalkayk3r on 2011-06-22
OK, so this is strange. I don't use Firefox much, my default browser is Google Chrome. But I've noticed sometimes things like Flash on some sites runs smoother in FireFox. So yesterday I opened up FF because Facebook was giving me some issues, so i wanted to see if it was Chrome or FB. Now, I haven't run FF in a few weeks, and I've noticed a few updates had rolled in for it since my last use.

When I opened FF and went to FB the login page wouldn't display correctly, and in fact would display no text whatsoever except for the links for the Japanese and Chinese FB pages. I assumed it was FB since I was already having issues with it. Later, I tried again and got the same loading issue. So I ran a Google search for FF issues with FB and got the same problem with Google search results, I got the logo and all the little search icons, but no text. 

I tried everything I could think of and everything anyone I asked could think of including:

[LIST]
[*]Renaming and/or removing ./mozilla
[*]running rm -rf .firefox
[*]uninstalling and reinstalling firefox
[*]removing firefox 4.01 and upgrading it to 5.0
[*]creating a new profile
[/LIST]

The only thing that I can do to make FF work is run **Alt+F2 gksu firefox**. That allows it work with out any issues. Has anyone come across this issue or anything similar? I'm including a couple screen shots of what it looks like when it's not working correctly. *Note: these pages have finished loading, the text isn't "white on white" it's just not displaying, view source of these pages shows the complete page is loaded including all text it just isn't being rendered.*

---

### Post by Habitual on 2011-06-22
One rule of troubleshooting goes like this:

If it works as root but not as the user, it is a permissions error.

Mine is 
700 jj users ~/.mozilla/firefox/*
644 jj users ~/.mozilla/firefox/profiles.ini

Yours may be jj:jj as I am on a different OS.

---

### Post by c0stalkayk3r on 2011-06-22
> **Habitual said:**
> One rule of troubleshooting goes like this:

If it works as root but not as the user, it is a permissions error.

Mine is 
700 jj users ~/.mozilla/firefox/*
644 jj users ~/.mozilla/firefox/profiles.ini

Yours may be jj:jj as I am on a different OS.

Yeah, I thought the same thing, but it doesn't seem to matter. I could set the permissions to full access on every FF related file and folder and it still does the same thing. :confused:

---

