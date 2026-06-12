---
title: "ugly tab color on Firefox"
date: 2011-11-13
forum: General Help
---

### Post by tanveers on 2011-11-13
I need help in fixing the ugly tab color of Firefox. As you can see in the attached screenshot that my active tab color is bluish. I am not using any theme. It should match the same color as the URL bar. Can anyone tell me how to fix this issue. I know it's not such a big deal and I can live with this but I need to get a more uniform Firefox look - the way it should be.

Thanks,

TS

---

### Post by vasa1 on 2011-11-13
> **tanveers said:**
> I need help in fixing the ugly tab color of Firefox. As you can see in the attached screenshot that my active tab color is bluish. I am not using any theme. It should match the same color as the URL bar. Can anyone tell me how to fix this issue. I know it's not such a big deal and I can live with this but I need to get a more uniform Firefox look - the way it should be.

Thanks,

TS

If you are comfortable editing userChrome.css, you could add this code and play with it:
```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
.tabbrowser-tab[selected="true"] {
	background-color:  #ffffff  !important;
	background-image: none !important; 
	}
.tabbrowser-tab:not([selected="true"]) {
	background-color: #555555 !important;  /*change to suit yourself*/
	background-image: none !important;
	}
```

I don't know how much you know or don't know and so this post is kinda short!

The other thing is the the Fx devs may change code often and so it's better to specify the Fx version you're using. This code works for Fx 7.0.1

If you have more requirements, it maybe useful to install the **Stylish** extension from AMO and visit [http://forum.userstyles.org/](http://forum.userstyles.org/) where the dev hangs out.

---

### Post by tanveers on 2011-11-13
> **vasa1 said:**
> If you are comfortable editing userChrome.css, you could add this code and play with it:
```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
.tabbrowser-tab[selected="true"] {
    background-color:  #ffffff  !important;
    background-image: none !important; 
    }
.tabbrowser-tab:not([selected="true"]) {
    background-color: #555555 !important;  /*change to suit yourself*/
    background-image: none !important;
    }
```I don't know how much you know or don't know and so this post is kinda short!

The other thing is the the Fx devs may change code often and so it's better to specify the Fx version you're using. This code works for Fx 7.0.1

If you have more requirements, it maybe useful to install the **Stylish** extension from AMO and visit [http://forum.userstyles.org/](http://forum.userstyles.org/) where the dev hangs out.


Thanks for your reply. I had a userChrome.css file. It had lot of stuff in it, not sure, how it got generated. First I made the backup of the original file then copied your code and played with the color a bit. It was working however, I still had this active tab not totally correct. Just for grins, I moved the userChrome.css file and renamed it. So basically no userChrome.css file and restarted Firefox and there I had the perfect tab (interface). I am going to keep it this way. I don't think I need userChrome.css file.

Thanks again for providing pointers to solve this problem. :D

TS

---

