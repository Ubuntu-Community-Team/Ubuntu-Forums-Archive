---
title: "Set workspace names missing in Gnome 10.10 Maverick"
date: 2010-11-07
forum: General Help
---

### Post by -pgg- on 2010-11-07
What has happened to the option to display names of each workspace on the lower panel bar?

Normally it was just a case of 'right click' any of the workspace and selecting 'Preferences', setting number of workspaces required and then using the name listbox to name each to desired title. In Maverick only the number of work places can be set; the list of names facility has been deleted from display. The current workspace name displays in the tooltip display as "workspace n", but there seems to be no easy way to change this title.

In 'gconf-editor' under schemas>apps>workspace_switcher_applet>prefs>display_workspace_names it only gives the system message "...can't be edited..."

---

### Post by stinkeye on 2010-11-07
I'm guessing your using compiz because when running compiz this option
isn't available because in reality your only running one desktop even though you may have 4 virtual desktops.

---

### Post by Cypher on 2010-12-06
Under XFCE, I can go to Settings and Workspaces and can indeed set the name of each of the workspaces, but that doesn't seem to be reflected on the panel..what gives??

Cheers

---

### Post by Red_Steve on 2010-12-06
> **-pgg- said:**
> What has happened to the option to display names of each workspace on the lower panel bar?

Normally it was just a case of 'right click' any of the workspace and selecting 'Preferences', setting number of workspaces required and then using the name listbox to name each to desired title. In Maverick only the number of work places can be set; the list of names facility has been deleted from display. The current workspace name displays in the tooltip display as "workspace n", but there seems to be no easy way to change this title.

In 'gconf-editor' under schemas>apps>workspace_switcher_applet>prefs>display_workspace_names it only gives the system message "...can't be edited..."

Running Metacity instead of Compiz would bring this functionality back while Compiz can't manage custom named workspaces (yet)

---

### Post by tropo on 2011-02-27
They are not missing! (SOLVED)

About to change the names of workspaces: Ubuntu 10.10. This is an easy way to do it:
Clicks in: System/ preference/appearance/ visual effects/ select "none".  
Now you can right click in the workspace/preference and you can change the names: double click in the name to change. (you can select in  "show workspace name in switcher)

Para cambiar los nombres de los sitios de trabajo: Ubunti 10.10. Este es un modo facil de hacerlo:
Presione: System/preferencias/apariencia/efectos visuales/ seleccione "ninguno"
Ahora con clic del botón derecho sobre los espacios de trabajo/ preferencia puede cambiar los nombre: presione doble clic en el nombre a cambiar (puede seleccionar "muestre los nombres en el cambiador)

---

