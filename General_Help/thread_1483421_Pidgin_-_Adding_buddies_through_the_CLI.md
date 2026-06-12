---
title: "Pidgin - Adding buddies through the CLI"
date: 2010-05-14
forum: General Help
---

### Post by ManiacDan on 2010-05-14
I recently began at a new company that uses google apps for domains.  The problem is, there are nearly 150 employees and no centralized address book to speak of.  I managed to get a list of legal names and email addresses out of the HR department, but I'd like to build my google address book as well as my pidgin buddy list.

Pidgin buddy lists are in the format:
```
		<group name='Advertising'>
			<setting name='collapsed' type='bool'>0</setting>
			<contact>
				<buddy account='myAccount@myCompany.com' proto='prpl-jabber'>
					<name>BobSmith@myCompany.com</name>
					<alias>Bob Smith</alias>
				</buddy>
			</contact>
			<contact>
				<buddy account='myAccount@myCompany.com' proto='prpl-jabber'>
					<name>JaneDoe@myCompany.com</name>
					<alias>Jane Doe</alias>
				</buddy>
			</contact>
		</group>
       //etc
```I've tried to simply edit blist.xml, but the act of actually ADDING a buddy does more than simply stick them into your list, it actually performs a server action to do mutual authentication and stuff.  So my question is: Is there a way I can run a script that will "add" all these people onto my buddy list without me having to type each email address and full name by hand?

Also, if we can do THAT, does anyone know how I can do the same to my google apps account?  I haven't actually looked at that yet.

-Dan

---

### Post by ManiacDan on 2010-05-14
Follow-up: importing contacts into gmail can be done easily through the "import" link, but be warned: Attempting to add a "department" column broke it for me (odd resulting behavior), I just filed a bug report with google.

Any thoughts on pidgin?  Adding contacts to google talk didn't fix it, even when selecting "show all contacts" in gtalk.

-Dan

---

