---
title: "Java help"
date: 2010-12-23
forum: General Help
---

### Post by tlf30 on 2010-12-23
I know this is not about ubuntu but this is the only place I know to ask this. I'm working on a login script and I'm trying to get it so user can press the enter key.
 
this is the code:
 
//imports
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;
import java.io.*;
import java.util.*;
//start
public class login extends JFrame implements ActionListener {
//creat buttons
JLabel status = new JLabel("Please enter your username & passowrd.");
JLabel userlabel = new JLabel("Username:");
JLabel passlabel = new JLabel("Password:");
JTextField user = new JTextField("", 10);
JPasswordField pass = new JPasswordField("", 10);
JButton logon = new JButton("login");
//create frame
public login() {
super("login");
setSize(250, 200);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
setResizable(false);
setTitle("Login");
FlowLayout flo = new FlowLayout();
setLayout(flo);
logon.addActionListener(this);
add(status);
add(userlabel);
add(user);
add(passlabel);
add(pass);
KeyMonitor monitor = new KeyMonitor(this);
addKeyListener(monitor);
add(logon);
setVisible(true);
}
class KeyMonitor extends KeyAdapter {
login display;
KeyMonitor(login display) {
this.display = display;
}
public void KeyTyped(KeyEvent event) {
String key1 = ("13");
String key = KeyEvent.getKeyText(13);
if(key1.equals(key)) {
try {
login1();
} catch (IOException ex) {
status.setText("Account dose not exist.");
setSize(200, 200);
}
}else {
System.out.println("your stuped");
}
 
}
}
public void actionPerformed(ActionEvent event) {
String command = event.getActionCommand();
if (command.equals("login")) {
//catch account dose not exist
try {
login1();
} catch (IOException ex) {
status.setText("Account dose not exist.");
setSize(200, 200);
}
}
}
//respond to button
public void login1() throws IOException {
//username ans password.
File account = new File(user.getText() + ".dat");
FileInputStream inStream = new FileInputStream(account);
Properties config = new Properties();
config.load(inStream);
String username1 = config.getProperty("username");
String password1 = config.getProperty("password");
//test username and pass
if (username1.equals(user.getText())&& password1.equals(pass.getText())) {
 
status.setText("loging on... Please wait...");
logon.setEnabled(false);
user.setEditable(false);
pass.setEditable(false);
setSize(200, 200);
repaint();
menu.main(null);
logon.setVisible(false);
System.out.println(user.getText() + " has logged on.");
System.out.println(user.getText() + "'s password is: " + pass.getText());
} else {
status.setText("Incorrect uername or password.");
repaint();
}
}
 
//creat window
public static void main(String[] arguments) {
login login1 = new login();
}
}

---

### Post by Spyderkid on 2010-12-23
[edit]

---

