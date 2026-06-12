---
title: "Default Icon for Filetypes?"
date: 2006-03-22
forum: General Help
---

### Post by Toxicity999 on 2006-03-22
How does one set the default Icon for any given file extension? In this case RMVB files. I'm sure its not that difficult but honestly... no clue. I actually use dapper but I'm sure it's universal on such a simple scale and I know it seems alot more people hang out here who could help as of now.

---

### Post by Ramses de Norre on 2006-03-22
I'd check the config file of your icon theme, it's normally in ~/.icons/theme_name/ and it's called theme.index or something like that. (I'm forced to work in win now so I can't check).
I think the icon folders are defined there and you'll need to paste the image for the filetype in the correct folder with the correct name.

If it's not defined in the conf file of your theme you need to make it or look for a line 'inherits=', the themes defined after that are used for icons not defined by the main theme and maybe you need to edit those themes conf file then.

---

### Post by psychicdragon on 2006-03-22
You'll need to copy one of the other video file icons to a file called gnome-mime-application-vnd.rn-realmedia-vbr.(png/svg) in your icon theme's mimetypes folder.

---

