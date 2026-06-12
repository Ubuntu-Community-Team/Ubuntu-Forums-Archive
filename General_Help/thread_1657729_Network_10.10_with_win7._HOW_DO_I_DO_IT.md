---
title: "Network 10.10 with win7. HOW DO I DO IT??"
date: 2011-01-01
forum: General Help
---

### Post by Duane A on 2011-01-01
Why is it SO difficult to network Ubuntu (last 4 versions) to Windows (xp pro) Win7. I have not been able to network any of these. I have no idea what is required and have searched--apparently not correctly--and see many "answers" but none that work for me.

Where do I get the definitive answer on networking Ubuntu 10.10 with my other computer using Win7 on MY ethernet in house, with no wireless, connection?

Which one do I start with 10.10 or win7, to start making the connection. The terminology for win7 is different than formerly acceptable WORKGROUP. I am completly lost.

This is my New Years Project. Make it yours and helpppppppppppp me please?

---

### Post by dcstar on 2011-01-02
> **Duane A said:**
> Why is it SO difficult to network Ubuntu (last 4 versions) to Windows (xp pro) Win7. I have not been able to network any of these. I have no idea what is required and have searched--apparently not correctly--and see many "answers" but none that work for me.

Where do I get the definitive answer on networking Ubuntu 10.10 with my other computer using Win7 on MY ethernet in house, with no wireless, connection?

Which one do I start with 10.10 or win7, to start making the connection. The terminology for win7 is different than formerly acceptable WORKGROUP. I am completly lost.

This is my New Years Project. Make it yours and helpppppppppppp me please?

What are you complaining about, what is your **specific** problem?

---

### Post by cariboo on 2011-01-02
You've got it backwards, Windows, especially a default Windows 7 system is hard to network with any other operating system. Windows only understands the smb protocol, whereas OSX and Linux can use many different networking protocols.

A default Win 7 system won't even network with XP. The first thing you need to do is go to Control Panel->Networks and Sharing and turn off the homegroup, once you've done that you can setup your Windows shares as you would in XP.

Once you done that, you need to install samba on your Ubuntu system in order for the Windows systems to be able to see the shares on your Ubuntu system. There are many samba howtos here on the forums, as well as [https://help.ubuntu.com]("https://help.ubuntu.com").

---

### Post by colin.p on 2011-01-02
It is amazing actually. 7 has to be the most difficult win version to network (out of the box) yet. It may work just fine with an all 7 network, but add anything else, even XP or vista, and it is a royal PITA.
It can be done, just a complete bother. However, I can see MS's point, buy all new computers complete with 7! :rolleyes:
However, an all ubuntu network is a peach.

---

