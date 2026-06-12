---
title: "Icecast and IDJC"
date: 2010-07-16
forum: General Help
---

### Post by jackopo on 2010-07-16
Hi Folks,

I'm trying to set up a internet radio streaming, where I can stream using Internet DJ Console.

I didn't found any tutorial or HowTo. So I'm asking if anyone could give me some help or recommend a good tutorial.

I started following this [HowTo]("http://www.ehow.com/how_5183447_make-radio-stream-ubuntu.html").

I don't really understand how to configure my icecast.xml file in oder to use the server with idjc.

Thanks

---

### Post by StephenF on 2010-07-19
> **jackopo said:**
> Hi Folks,

I'm trying to set up a internet radio streaming, where I can stream using Internet DJ Console.

I didn't found any tutorial or HowTo. So I'm asking if anyone could give me some help or recommend a good tutorial.

I started following this [HowTo]("http://www.ehow.com/how_5183447_make-radio-stream-ubuntu.html").

I don't really understand how to configure my icecast.xml file in oder to use the server with idjc.

Thanks
You have it backwards. 

You configure IDJC to use the Icecast server, not the other way around. Anyway, the only things you need to alter in the standard Icecast2 configuration file are the passwords marked hackme in the authentication section. You will need to use the same source password in IDJC later in order to stream.

Launching icecast as a normal user is as easy as.
$ icecast -c /path/to/icecast.xml

If you intend launching Icecast2 from an init script at boot you will also need to set the changeowner values in the security section at the end of the file to user:icecast2, group:icecast.

And finally, a link to some proper documentation:
[http://www.icecast.org/docs/icecast-2.3.2/icecast2_config_file.html](http://www.icecast.org/docs/icecast-2.3.2/icecast2_config_file.html)

---

### Post by jackopo on 2010-07-21
I think that I don't configure well the icecast server.

I keep getting this error in the error.log file

```
INFO admin/admin_handle_request Bad or missing password on mount modification admin request (command: listclients)
WARN admin/admin_handle_request Admin command listclients on non-existent source /stream
```

I've tried everything, but now i'm really lost.

How do I configure exactly the icecast.xml file in order to use icecast with idjc?

---

