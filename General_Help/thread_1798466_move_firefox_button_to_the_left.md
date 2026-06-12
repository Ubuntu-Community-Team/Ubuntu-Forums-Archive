---
title: "move firefox button to the left??"
date: 2011-07-06
forum: General Help
---

### Post by jeremija on 2011-07-06
Hello, is it possible to move the firefox button to the left?

On my other ubuntu PC it is already to the left of the tabs by default, but I'm not able to drag it to the right...

[img]http://www.deviantpics.com/images/screentft.png[/img]

---

### Post by bug67 on 2011-07-06
Try using the extention, ["Movable Firefox Button"](https://addons.mozilla.org/en-US/firefox/addon/movable-firefox-button/).  Lets you put the button anywhere you want.

---

### Post by jeremija on 2011-07-06
Thanks, I just changed/added the two values in browserOverlay.css in the addon zip file (.xpi) to hide the firefox icon from the button and add the text:

```
.titlebar-placeholder[type="appmenu-button"] {
	display: none;
}

#appmenu-toolbar-button,
#appmenu-button {
	padding: 0 5px;
	min-width: 0;
}

toolbar:not([mode="text"]) #appmenu-toolbar-button > .toolbarbutton-icon,
toolbar:not([mode="text"]) #appmenu-button > .button-box .button-icon {
[B]	/*list-style-image: url("chrome://branding/content/icon16.png");*/
	list-style-image: none;[/B]
}

toolbar[mode="icons"] #appmenu-toolbar-button > .toolbarbutton-text,
toolbar[mode="icons"] #appmenu-button > .button-box .button-text {
[B]	/*display: none;*/
	content: "Firefox";[/B]
}

window[selectedSkin="classic/1.0"] #appmenu-container #appmenu-button {
	border-radius: 4px;
	border-top: 1px solid rgba(83,42,6,.9);
}



window[selectedSkin="classic/1.0"][privatebrowsingmode=temporary] #appmenu-container  #appmenu-button {
	border-color: rgba(43,8,65,.9);
}

window[selectedSkin="classic/1.0"] #appmenu-container #appmenu-button:hover:not(:active):not([open]) {
	border-color: rgba(83,42,6,.9);
}

window[selectedSkin="classic/1.0"][privatebrowsingmode=temporary] #appmenu-button:hover:not(:active):not([open]) {
	border-color: rgba(43,8,65,.9);
}

window[selectedSkin="classic/1.0"] #appmenu-container #appmenu-button:hover:active,
window[selectedSkin="classic/1.0"] #appmenu-container #appmenu-button[open] {
	border-radius: 0;
}

@media all and (-moz-windows-theme:aero) {
	window[selectedSkin="classic/1.0"] #appmenu-container #appmenu-button {
		border-top-width: 2px;
		margin-bottom: 0;
		-moz-border-top-colors: rgba(255,255,255,.5) rgba(83,42,6,.9);
	}

	#main-window[selectedSkin="classic/1.0"][privatebrowsingmode=temporary] #appmenu-button {
		-moz-border-top-colors: rgba(255,255,255,.5) rgba(43,8,65,.9);
	}
}
```

You can uncomment the display-none and delete the content: "Firefox" line to make the button take less space and just have a down arrow.

[IMG]http://www.deviantpics.com/images/screennzn.png[/IMG]

It's funny that the button stays there even after disabling the addon :)

---

