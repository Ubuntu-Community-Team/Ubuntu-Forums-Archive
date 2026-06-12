---
title: "Dark Gtk theme screws up Firefox 4.0"
date: 2011-04-26
forum: General Help
---

### Post by Skyxn3t on 2011-04-26
Using dark gtk themes changes the background color of common form controls (input boxes, text boxes, radio buttons, etc...) into the same dark color used in the theme, so you end up with dark controls with black text, which makes them unreadable.

While searching I found that there's a way to make Firefox override the system colors, and that is by creating a  **userContent.css** file in **/home/user_name/.mozilla/firefox/profile.default/chrome**

Here's the **userContent.css** file:
```

body {
background-attachment: scroll !important;
}

input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}

```[SIZE=3]This css code fixes text boxes, input boxes, etc... but I still have dark radio buttons, dark check boxes, and dark drop down menus, does anyone know what might be causing this problem?[/SIZE]


Examples:
[IMG]http://i901.photobucket.com/albums/ac211/0xGFX007/001.png[/IMG]

[IMG]http://i901.photobucket.com/albums/ac211/0xGFX007/002.png[/IMG]

---

### Post by Skyxn3t on 2011-04-26
[http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

---

