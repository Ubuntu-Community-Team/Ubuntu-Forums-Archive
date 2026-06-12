---
title: "automatic website login"
date: 2010-06-20
forum: General Help
---

### Post by desmane on 2010-06-20
Hello people, 

I am trying to write a script that does a automatic login on a html website that looks like this: 

```
<form action="here/the/link/to/website.html" method="POST">
						<input name="beilage" value="" type="hidden">
						<div class="eP_head_Link">
							Benutzername<br><input name="username" size="15" value="" style="width: 160px;" type="text"><br><br>
							
							Kennwort<br><input name="passwort" size="15" value="" style="width: 160px;" type="password"><br>

							<input name="version" value="pdf" type="hidden">
							<input class="formButton" name="Ok" value="Ok" type="submit">
						</div>
					</form>

```

From there, I would like to download a zip file which is provided always under the same link that looks like this: 

```
http://domain.com/getfiles_complete.php?name=NAME&name2=&NAME2=&Y=10&M=06&D=19

```
I couldnt figure out wget on this one because you are dereferred to a filename that is different every time you click.

Of course I have the credentials for that website and do not intend to do anything illegal, this script will be for convenience purposes. Any help is highly appreciated!

Thanks a lot!

---

