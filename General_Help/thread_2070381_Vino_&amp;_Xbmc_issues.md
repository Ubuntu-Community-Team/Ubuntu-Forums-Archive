---
title: "Vino &amp; Xbmc issues"
date: 2012-10-12
forum: General Help
---

### Post by hth0923 on 2012-10-12
Hi All,

Many thanks for looking at this thread.

I am using vino remote access server & xbmc on Ubuntu 12.04. Everything works nicely without any problems. Recently, I have looked at htop over the terminal, and I have discovered when I access the vino server the CPU usage shows around 20%, and when disconnect vnc access from the client software, the cpu shows around 90%. please find the screen shots below,

**_[SIZE="3"]With accessing the vino:[/SIZE]_**
[IMG]http://img.photobucket.com/albums/v146/hth0923/open_zpsbc2d0464.png[/IMG]

**_[SIZE="3"]Without accessing the vino:[/SIZE]_**
[IMG]http://img.photobucket.com/albums/v146/hth0923/close_zpsc653742e.png[/IMG]

Please advise!

Deeply appreciate and thanks in advance!

Regards,

---

### Post by hth0923 on 2012-10-12
Any one could give me a help here?

Do you need any log files or any other information?

Thanks in advance!

Regards,

---

### Post by kirichkov on 2012-10-21
I assume you are running the default install of xbmc with the default skin (Confluence).

The issue is caused by the news ticker at the bottom. Here's the easiest way to fix it:

1. Go to Settings > Appearence > Skin
2. On the right side untick "Show RSS news feeds"

You can, alternatively, also change the skin.

---

### Post by hth0923 on 2012-10-21
Many thanks for your answers.

At the moment, XBMC shows 9% which i think it is much better than 23%, but Vino still showing 90% when XBMC is running.

---

### Post by kirichkov on 2012-11-18
> **hth0923 said:**
> Many thanks for your answers.

At the moment, XBMC shows 9% which i think it is much better than 23%, but Vino still showing 90% when XBMC is running.

I just noticed the same issue, so I decided to stop using vino and switch to x11vnc. I did a brief test and it seems x11vnc doesn't exhibit these issues. Even if connected while a movie is playing it still has lower cpu footprint then vino -20-30% on a Dual Core 1.2GHz CULV Intel.

Here's what I did to get it up and running:
1. Start the *Screen sharing* configurator and disable screen sharing.
2. Install x11vnc & xinetd
```

$ sudo apt-get install x11vnc xinetd

```
3. Go to /etc/xinetd.d/ and create a new file with the following content:
```

x11vncservice
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -display :0 -auth /var/run/lightdm/root/:0 -q
        disable         = no
}

```
4. Start the xinetd service
```

$ sudo start xinetd

```

---

### Post by hth0923 on 2012-11-18
> **kirichkov said:**
> I just noticed the same issue, so I decided to stop using vino and switch to x11vnc. I did a brief test and it seems x11vnc doesn't exhibit these issues. Even if connected while a movie is playing it still has lower cpu footprint then vino -20-30% on a Dual Core 1.2GHz CULV Intel.

Here's what I did to get it up and running:
1. Start the *Screen sharing* configurator and disable screen sharing.
2. Install x11vnc & xinetd
```

$ sudo apt-get install x11vnc xinetd

```
3. Go to /etc/xinetd.d/ and create a new file with the following content:
```

x11vncservice
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -display :0 -auth /var/run/lightdm/root/:0 -q
        disable         = no
}

```
4. Start the xinetd service
```

$ sudo start xinetd

```

It didn't work for me, but I have found a link, it works great! Please find it below,

[http://unquietwiki.blogspot.co.uk/2012/03/another-way-to-use-vnc-with-ubuntu.html](http://unquietwiki.blogspot.co.uk/2012/03/another-way-to-use-vnc-with-ubuntu.html)

Many thanks for the idea!

---

