---
title: "Delete recent documents"
date: 2006-03-26
forum: General Help
---

### Post by ubuntuubuntu on 2006-03-26
How do I delete the recent documents? When I use " Places -> recent documents -> clear recent documents" , the recent documents still appear on programs like OpenOffice and Adobe Reader.

---

### Post by eriefisher on 2006-03-26
I think that just clears the list and does not actually delete the docs. You will have to go in and delete the actual file.

eriefisher

---

### Post by ubuntuubuntu on 2006-03-26
[QUOTE=eriefisher]I think that just clears the list and does not actually delete the docs. You will have to go in and delete the actual file.

eriefisher[/QUOTE]

I'm sorry... I wasn't clear enough. What I want is to clear the list, not the files. But doing this way, the listt from openoffice and adobe reader are not cleares.

---

### Post by nixclusive on 2006-03-26
Open the terminal:

```
sudo rm -f $HOME/.recently-used
sudo touch $HOME/.recently-used
sudo chmod 000 $HOME/.recently-used
```
No recent documents will be created.

---

### Post by ubuntuubuntu on 2006-03-26
[QUOTE=nixclusive]Open the terminal:

```
sudo rm -f $HOME/.recently-used
sudo touch $HOME/.recently-used
sudo chmod 000 $HOME/.recently-used
```
No recent documents will be created.[/QUOTE]

It doesn't work. It deletes the list from " Places -> Recent Documents" . These I have already deleted. What I want to delete is the list in the OpenOffice Writer (File -> Recent documents) and from Adobe reader (file).

---

