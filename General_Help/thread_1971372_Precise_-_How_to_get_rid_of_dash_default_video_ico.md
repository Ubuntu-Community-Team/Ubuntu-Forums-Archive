---
title: "Precise - How to get rid of dash default video icons?"
date: 2012-05-02
forum: General Help
---

### Post by egalua on 2012-05-02
I just installed precise: by default, the "Video" section in dash is populated by videos from many sources.

I find this very annoying.

How do I delete all this videos?

More generally, is there a way to configure dash behaviour?

Thanks a lot.

---

### Post by mc4man on 2012-05-02
If you don't want to use the remote videos then remove the package - 
unity-scope-video-remote 

If wishing to keep but not see then open  Videos in the Dash > filter results > Sources and select 'My Videos'

This setting will hold for the rest of session though on fresh logins the Results will unfortunately  return to Sources > All 

There are limited (very),  Dash/Lens  options available in gsettings, screen shows general location in dconf-editor & one of the few options for apps lens

---

### Post by egalua on 2012-05-02
Thank you: removing unity-scope-video-remote did it.

---

