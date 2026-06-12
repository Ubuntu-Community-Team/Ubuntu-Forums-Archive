---
title: "ask about midori"
date: 2012-05-31
forum: General Help
---

### Post by dik angga on 2012-05-31
hi master, i have midori browser, but i confused why my midori is lag for some sites..?like this ubuntuforum, 9gag, and many sites. LAG when i scroll down.
why..??

---

### Post by vasa1 on 2012-06-01
> **dik angga said:**
> hi master, i have midori browser, but i confused why my midori is lag for some sites..?like this ubuntuforum, 9gag, and many sites. LAG when i scroll down.
why..??
Do you have a specific need to use Midori?

I've seen that both Midori and Epiphany do not play well with certain sites. I've not noticed the lag in scrolling down but I've seen the CPU usage rise for no apparent reason for more sites than I'm comfortable with.

So while I haven't uninstalled Midori, I plan on restricting my use of it.

It's a great little browser and has improved tremendously over time. I just wish it didn't go crazy on some sites.

BTW, I'm on the dev version from the Launchpad ppa.

(And yes, I've stuck in the box-shadow bit.)

---

### Post by Bouvet on 2012-06-01
I've tried Midori and really like it, but, the browser crashes a lot 
on me so I sadly have to dump it.

---

### Post by dik angga on 2012-06-01
> **vasa1 said:**
> Do you have a specific need to use Midori?

I've seen that both Midori and Epiphany do not play well with certain sites. I've not noticed the lag in scrolling down but I've seen the CPU usage rise for no apparent reason for more sites than I'm comfortable with.

So while I haven't uninstalled Midori, I plan on restricting my use of it.

It's a great little browser and has improved tremendously over time. I just wish it didn't go crazy on some sites.

BTW, I'm on the dev version from the Launchpad ppa.

(And yes, I've stuck in the box-shadow bit.)
midori is fast for me.. :D but i sad midori like that
> **Bouvet said:**
> I've tried Midori and really like it, but, the browser crashes a lot 
on me so I sadly have to dump it.
i feel ur pain brother hehehe

---

### Post by dino99 on 2012-06-01
basicly satisfied here on i386, some crashes when too much tabs are opened at the same times.

check that the graphic driver is well activated (sudo jockey-gtk)

---

### Post by vasa1 on 2012-06-01
> **dino99 said:**
> ...
check that the graphic driver is well activated (sudo jockey-gtk)

I got this:
```

(jockey-gtk:14570): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:14570): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

```

A pop-up window also appeared telling me that a proprietary Broadcom driver is in use.

Can you explain? (I don't have any browsing problems with Chrome or Firefox.)

---

### Post by dik angga on 2012-06-01
i never got that eror..and never crashed when open many tab..
my problem just some sites is lag on midori like this forum, so hard to scroll down the page

---

### Post by vasa1 on 2012-06-01
> **dik angga said:**
> i never got that eror..and never crashed when open many tab..
my problem just some sites is lag on midori like this forum, so hard to scroll down the page

One possibility is that some sites employ images or CSS that are resource-heavy. The Midori devs point to **boxshadow** being one bit of CSS that can cause problems. As the gimmicks made available by CSS3 get more popular, those with older or less-powerful machines will find surfing the net increasingly difficult.

If you want to continue using Midori on your present kit, I suggest you get a bit familiar with html and CSS and turn off a lot of "features" that web designers seem to think add value but which can cause issues for people whose hardware is not the latest and greatest.

---

### Post by dik angga on 2012-06-02
> **vasa1 said:**
> One possibility is that some sites employ images or CSS that are resource-heavy. The Midori devs point to **boxshadow** being one bit of CSS that can cause problems. As the gimmicks made available by CSS3 get more popular, those with older or less-powerful machines will find surfing the net increasingly difficult.

If you want to continue using Midori on your present kit, I suggest you get a bit familiar with html and CSS and turn off a lot of "features" that web designers seem to think add value but which can cause issues for people whose hardware is not the latest and greatest.
i don't get it..
how the way to turn off that..?? and after i turn off that, my midori can go normal?

---

### Post by vasa1 on 2012-06-02
> **dik angga said:**
> i don't get it..
how the way to turn off that..?? and after i turn off that, my midori can go normal?
Exit Midori. Open a file manager, Thunar or whatever:
You should see something like this:
/home/your_name/.local/share/midori/styles
In there, there should be a file called my-user-style.css which is a plain text file. If the folder is empty, you can create the file using a text editor.
Place this in it:```
* 
{
-webkit-box-shadow: none !important;
}

```
Save the file.

Restart Midori and hope the problem goes away.

[http://ubuntuforums.org/showthread.php?t=1988734](http://ubuntuforums.org/showthread.php?t=1988734)

---

### Post by dik angga on 2012-06-02
> **vasa1 said:**
> Exit Midori. Open a file manager, Thunar or whatever:
You should see something like this:
/home/your_name/.local/share/midori/styles
In there, there should be a file called my-user-style.css which is a plain text file. If the folder is empty, you can create the file using a text editor.
Place this in it:```
* 
{
-webkit-box-shadow: none !important;
}

```
Save the file.

Restart Midori and hope the problem goes away.

[http://ubuntuforums.org/showthread.php?t=1988734](http://ubuntuforums.org/showthread.php?t=1988734)
i didn't found midori folder in /home/my_name/.local/share/

---

### Post by vasa1 on 2012-06-02
> **dik angga said:**
> i didn't found midori folder in /home/my_name/.local/share/
Then just create the folder, subfolder, and file.

Big oops: You also need to enable "User addons" in preferences. **Do that first**. Maybe the necessary folders will be created. Read the link I gave or [http://wiki.xfce.org/midori/faq:](http://wiki.xfce.org/midori/faq:)
> 
Scrolling on website xyz is very slow

    Go to Tools > Extensions
    Enable 'User Addons' if it's not yet enabled
    Create a text file .local/share/midori/styles/scrollfix.user.css
    Put this into the file: * {-webkit-box-shadow: none !important;}



---

