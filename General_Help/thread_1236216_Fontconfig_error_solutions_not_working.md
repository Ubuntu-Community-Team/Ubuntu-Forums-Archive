---
title: "Fontconfig error solutions not working"
date: 2009-08-10
forum: General Help
---

### Post by akrchstn on 2009-08-10
Okay so I am using awesome wm and I have taken up starting things though terminal but everything I start there will be a fontconfig error (Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed) but I have searched this already and none of the solutions are working. Here is my fonts.conf
```
<?xml version=”1.0&#8243;?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

---

### Post by akrchstn on 2009-08-10
...bump

---

