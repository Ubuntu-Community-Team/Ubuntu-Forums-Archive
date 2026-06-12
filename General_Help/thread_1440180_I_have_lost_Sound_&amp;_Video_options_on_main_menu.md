---
title: "I have lost Sound &amp; Video options on main menu"
date: 2010-03-27
forum: General Help
---

### Post by jcorden on 2010-03-27
Hi
I have been messing about with my system but have lost the Sound & Video options on the main desktop menu. How can I restore these, the programs are still there but I can't access them via the menu?
Thanks

---

### Post by tom4everitt on 2010-03-27
Check if you can activate them again in System->Preferences->Main Menu

---

### Post by jcorden on 2010-03-27
I've checked that, the options are not available.

All suggestions welcomed

Thanks

---

### Post by jcorden on 2010-03-27
Bump

---

### Post by tom4everitt on 2010-03-27
Is gnome-volume-control what you're looking for?

---

### Post by jcorden on 2010-03-27
Fixed it myself

this was my applications.menu file in ~/.config/menus

I removed the <Deleted/> in the Multimedia menu 

Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Multimedia</Name>
		<Deleted/>
	</Menu>
	<Menu>
		<Name>Games</Name>
	</Menu>
	<Menu>
		<Name>Accessories</Name>
	</Menu>
	<Layout>
		<Merge type="menus"/>
		<Menuname>Debian</Menuname>
		<Menuname>Accessories</Menuname>
		<Menuname>Education</Menuname>
		<Menuname>Games</Menuname>
		<Menuname>Graphics</Menuname>
		<Menuname>Internet</Menuname>
		<Menuname>Office</Menuname>
		<Menuname>Other</Menuname>
		<Menuname>Development</Menuname>
		<Menuname>Samsung Unified Driver</Menuname>
		<Menuname>System</Menuname>
		<Menuname>Universal Access</Menuname>
		<Menuname>wine-wine</Menuname>
		<Separator/>
		<Filename>gnome-app-install.desktop</Filename>
		<Merge type="files"/>
	</Layout>
	<Menu>
		<Name>Universal Access</Name>
		<Exclude>
			<Filename>orca.desktop</Filename>
		</Exclude>
		<AppDir>/home/james/.local/share/applications</AppDir>
	</Menu>
	<DefaultLayout inline="false"/>
	<Menu>
		<Name>alacarte-made</Name>
		<Directory>alacarte-made.directory</Directory>
		<Deleted/>
	</Menu>
	<AppDir>/home/james/.local/share/applications</AppDir>
	<Include>
		<Filename>alacarte-made.desktop</Filename>
	</Include>
	<Menu>
		<Name>Other</Name>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<DirectoryDir>/home/james/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<DirectoryDir>/home/james/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<DirectoryDir>/home/james/.local/share/desktop-directories</DirectoryDir>
	</Menu>
</Menu>

---

