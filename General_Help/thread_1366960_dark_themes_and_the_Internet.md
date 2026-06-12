---
title: "dark themes and the Internet"
date: 2009-12-29
forum: General Help
---

### Post by Strongman332 on 2009-12-29
hi I have recently started using a dark theme and I noticed that some times input boxes have wide black lines around them. also some buttons on some websites are black. are their any known fixes

fist screen shot is with a dark theme

second is with out

---

### Post by Strongman332 on 2009-12-29
bump

---

### Post by underquark on 2009-12-29
I think some boxes actually have two elements - a black line and a grey line.  Your dark theme has rendered the grey black.  similarly, some buttons are grey but your theme has grey more of a black.  Is this a custom theme of your own or an "off-the-shelf" one?

---

### Post by Strongman332 on 2009-12-29
it was shiki dark mint from gnome look but I have noticed every dark theme I try does this.

---

### Post by HappyFeet on 2009-12-29
Using a theme other than what is given to you by default is questionable at best. They are not 100% accurate in rendering certain things. These themes do not have the blessing of canonical, and are "use at your own risk."

---

### Post by sigurnjak on 2009-12-29
I use this :
[http://www.getpersonas.com/en-US/gallery/All/search?p=shiki&search.x=0&search.y=0](http://www.getpersonas.com/en-US/gallery/All/search?p=shiki&search.x=0&search.y=0)


and it looks great !

---

### Post by Strongman332 on 2010-01-05
> **HappyFeet said:**
> Using a theme other than what is given to you by default is questionable at best. They are not 100% accurate in rendering certain things. These themes do not have the blessing of canonical, and are "use at your own risk."

I realize that conical does not support themes don't render anything their gtk+ engines do, I figured sense shiki dark was based on shiki which is in the Ubuntu repos it would be fine for most things. but evidently it does not handle dark colors well. it maybe a limitation in gtk+. after-all, most users use lighter themes.

still looking for a theming engine to work around this issue if any one has any ideas let me know.

---

### Post by jwbrase on 2010-01-05
It's basically because Web browsers tend to display certain elements (buttons, text boxes, etc.) according to the System theme, and other elements according to what's specified on the Web page. This can lead to clashes if you use a theme that's dramatically different from most Web page color schemes.

You might want to try Opera: Except for window decoration, it ignores the System theme and uses a more neutral theme, which, since it's getting Web pages from a source that doesn't know about your System theme, is a good thing for a Web browser to do. Then again, I wasn't really looking into aesthetic considerations when I decided I liked Opera better than Firefox, so YMMV.

---

### Post by fragos on 2010-01-05
As it turns out this is a web site bug. Some web sites make assumptions about default backgrounds and font colors that aren't always correct. In some cases, some but not all of the defaults come from the system theme. As a web designer I never depend on defaults and set all visual aspects myself insuring proper rendering. This may also vary by browser. You're more likely to see this problem with dark themes that have close to white font colors.

---

### Post by Strongman332 on 2010-01-07
fragos fortunately i never had readability problems, however I see your point. I don't think i will be switching to opera though. so i might just have to get used to it or switch to lighter themes.

thank you for all of your help

---

### Post by fragos on 2010-01-07
> **Strongman332 said:**
> fragos fortunately i never had readability problems, however I see your point. I don't think i will be switching to opera though. so i might just have to get used to it or switch to lighter themes.

thank you for all of your help

I created a color scheme with colored backgrounds that still allowed enough contrast with darker colored fonts. If you will, I chose a font color that was readable both on white and my theme's background color.

---

