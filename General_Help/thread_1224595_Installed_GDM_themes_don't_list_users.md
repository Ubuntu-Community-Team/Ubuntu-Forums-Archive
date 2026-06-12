---
title: "Installed GDM themes don't list users"
date: 2009-07-27
forum: General Help
---

### Post by BoardStupid on 2009-07-27
So basically what the title says.

I have installed a few new GDM themes and have chosen ones primarily with a list of users on the computer, however, none of them are displaying any usernames at login.

I can still login just fine by typing name/pass but ideally I would prefer to have everyone listed (It's an ease of access thing for the other users).

The following is the xml file that came with the theme.```
<?xml version="1.0"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">



<greeter>

	<!-- background basecolor -->
	<item type="rect">
		<pos x="0" y="0" width="100%" height="100%"/>
		<!--change this if you want another color-->
		<normal color="#aaaaaa"/>
	</item>


	<!-- background pixmap image -->
	<!-- If you want another background image-->
	<!-- or you could get rid of this and just have a base color (from above)-->
	<item type="pixmap">
		<!-- Point this to another file -->
		<normal file="Elementary-Wall-1440-black.png"/>
		<pos x="0" y="0" width="100%" height="100%"/>
	</item>
	<!-- List Window container -->
	<item type="rect">
		
	<pos anchor="center" x="30%" y="50%" width="267" height="300"/>
		<fixed>
			<!-- login window pixmap -->
			<item type="pixmap">
			<normal file="list_box.png"/>
			<pos anchor="center" x="50%" y="50%"/>
			</item>

			<!-- userlist -->
			<item type="list" id="userlist">
			<pos x="3%" y="10%" width="250" height="300" anchor="nw"/>
			<color iconcolor="#ffffff" labelcolor="#ffffff"/>
			</item>

		</fixed>
	</item>
	<!-- login window container -->
	<item type="rect">
		
		<pos anchor="center" x="65%" y="50%" width="550" height="462"/>
		<fixed>


		<!-- login window pixmap -->
		<item type="pixmap">
			<normal file="main_box.png"/>
			<pos anchor="center" x="50%" y="50%"/>
		</item>
	

		<!-- Linux & hostname container -->
		<item type="rect">
				
			<pos anchor="n" x="50%" y="145"/>
			<normal color="#ff0000"/>
				
			<box orientation="vertical">
				
				<!--  Label -->
				<item type="label">
					<pos anchor="n" x="50%"/>
					<normal color="#696969" font="Arial 25"/>
					<!--  Change this to whatever you want. i.e. Suse Linux etc -->
					<text>elementary desktop</text>
				</item>
					
				<!-- Hostname label and Clock-->
				<item type="label">
					<pos anchor="n" x="0%"/>
					<normal color="#464646" font="Arial 8" alpha="0.5"/>
					<!--  The %h is the hostname and the %c is the clock -->
					<text>Welcome to %h  %c</text>
				</item>
			</box>
		</item>


		<!-- CAPS-LOCK warning -->
		<item type="label" id="caps-lock-warning">
			<pos anchor="n" x="50%" y="250"/>
			<normal font="Arial bold 8" color="#e84949" alpha="0.9"/>
			<stock type="caps-lock-warning"/>
		</item>
			
		<!-- error messages -->
		<item type="label" id="pam-error">
			<pos anchor="n" x="50%" y="500"/>
			<normal font="Arial bold 10" color="#e84949"/>
			<text></text>
		</item>


				<!-- username/password label -->
				<item type="label" id="pam-prompt">
					<pos anchor="e" x="43%" y="50%" />
					<stock type="username-label"/>
					<normal color="#525252" font="Arial 9 Bold"/>
				</item>




				 <!-- username/password entry -->
				<item type="entry" id="user-pw-entry">
					<pos anchor="w" x="44.8%" y="50%" />
					<normal color="#525252" font="Arial 9 Bold"/>
					<pos width="166" height="20"/>
				</item>
			
	
		<!-- button container -->
		<item type="rect">
			
			<pos x="50%" y="430" anchor="s" width="box" height="box"/>
		
			<box orientation="horizontal" spacing="20">
				
				<!-- lang button -->
				<item type="rect" id="language_button" button="true">
					<pos anchor="nw" width="32" height="32"/>
						
						<box orientation="vertical" spacing="0">
		
							<!-- button image -->
							<item type="pixmap">
								<normal file="lang.png" alpha="0.8"/>
								<prelight file="lang.png"/>
								<pos x="50%" anchor="n"/>
							</item>

							<!-- button text-label -->
							<item type="label">
								<pos x="50%" y="12" anchor="s"/>
								<normal color="#464646" font="Arial 8" alpha="0"/>
								<prelight color="#464646" font="Arial 8" alpha="0.5"/>
								<stock type="language"/>
							</item>
						</box>
				</item>
	
				<!-- session button -->
				<item type="rect" id="session_button" button="true">
					<pos anchor="nw" width="32" height="32"/>
						
					<box orientation="vertical" spacing="0">
		
						<!-- button image -->
						<item type="pixmap">
							<normal file="sess.png" alpha="0.8"/>
							<prelight file="sess.png"/>
							<pos x="50%" anchor="n"/>
						</item>

						<!-- button text-label -->
						<item type="label">
							<pos x="50%" y="12" anchor="s"/>
							<normal color="#464646" font="Arial 8" alpha="0"/>
							<prelight color="#464646" font="Arial 8" alpha="0.5"/>
							<stock type="session"/>
						</item>
					</box>
				</item>


				<!-- reboot button -->
				<item type="rect" id="system_button" button="true">
					<pos anchor="nw" width="32" height="32"/>
					
					<box orientation="vertical" spacing="0">
		
						<!-- button image -->
						<item type="pixmap">
							<normal file="cfg.png" alpha="0.8"/>
							<prelight file="cfg.png"/>
							<pos x="50%" anchor="n"/>
						</item>

						<!-- button text-label -->
						<item type="label">
							<pos x="50%" y="12" anchor="s"/>
							<normal color="#464646" font="Sans Arial Tahoma 8" alpha="0"/>
							<prelight color="#464646" font="Sans Arial Tahoma 8" alpha="0.5"/>
							<stock type="system"/>
						</item>
					</box>
				</item>
				
				</box>
			</item> 
		</fixed>
	</item>
</greeter>
```

Now, this is nothing against the author, I'm just wondering if the code is sound and it's my system that's at fault (which is more likely the case as it's the same result for three login windows).

To install this particular theme, I downloaded the tar.gz from [http://www.gnome-look.org/content/show.php/Elementary+GDM+List?content=86959]("http://www.gnome-look.org/content/show.php/Elementary+GDM+List?content=86959").

I then went System > Administration > Login Window, clicked on local and added the archive from the desktop.

I had a look around /etc/gdm for any signs of trouble but in all honesty I have no idea what would be classed as trouble and what is the norm.

Any help would be much appreciated.

---

### Post by CatKiller on 2009-07-27
> **BoardStupid said:**
>  I have installed a few new GDM themes and have chosen ones primarily with a list of users on the computer, however, none of them are displaying any usernames at login.

You need to select "Themed with Face Browser" in the Style drop-down box if you want the users to be displayed.

---

### Post by BoardStupid on 2009-07-27
Haha, of course it's as simple as that. Thanks for pointing that one out mate.

---

### Post by CatKiller on 2009-07-27
No worries.

---

### Post by deanrd on 2009-11-17
I have the faces on a login window from importing accounts on install, but the import apparantly didn't work correctly and my account has my daughters picture.

Where is the picture changed for the user?  I can't seem to find it.

Thanx - Dean

---

### Post by Vaphell on 2009-11-17
in my 9.04 it's in system->preferences->about me (or something like that)

---

### Post by deanrd on 2009-11-17
Thanx - got it!  I wish I knew where it was getting her picture from though as it doesn't appear to have a link to anything and its not loaded locally.  Enquiring minds want to know...  So much and so little time...

---

