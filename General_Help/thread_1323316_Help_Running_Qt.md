---
title: "Help Running Qt"
date: 2009-11-11
forum: General Help
---

### Post by frs89 on 2009-11-11
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] 				**Help: running Qt  - building a gui** 			
 			 			 		   		 		 		Hi
I'm new to ubuntu and Qt. I've installed Qt designer/assistant/linguist
I want to make this small Gui that I found on a tutorial

 #include <QApplication>
 #include <QPushButton>

 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);

     QPushButton hello("Hello world!");

     hello.show();
     return app.exec();
 }

When I make

flavio@flavio-laptop:~/Desktop$ cc gui.c -o gui
gui.c:1:25: error: QApplication: No such file or directory
gui.c:2:24: error: QPushButton: No such file or directory
gui.c: In function ‘main’:
gui.c:6: error: ‘QApplication’ undeclared (first use in this function)
gui.c:6: error: (Each undeclared identifier is reported only once
gui.c:6: error: for each function it appears in.)
gui.c:6: error: expected ‘;’ before ‘app’
gui.c:8: error: ‘QPushButton’ undeclared (first use in this function)
gui.c:8: error: expected ‘;’ before ‘hello’
gui.c:9: error: ‘hello’ undeclared (first use in this function)
gui.c:12: error: ‘app’ undeclared (first use in this function)

I don't know who to compile the code.[FONT=Verdana]What I'm supposed to do?

Note: I don't want to use any IDE, just trough command line.

Thanks[/FONT]

---

