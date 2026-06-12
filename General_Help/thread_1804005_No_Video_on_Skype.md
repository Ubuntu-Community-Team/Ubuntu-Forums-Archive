---
title: "No Video on Skype"
date: 2011-07-14
forum: General Help
---

### Post by demma on 2011-07-14
Hi All
     Im very new to Linux so go easy on me,,everything works on Skype except the Webcam, the cam works ok on other webcam software.
Im using Ubuntu 11.04 .
                     Demma

---

### Post by macaholic on 2011-07-14
Have you tried going into the Skype video preferences to see if it shows up in there?

---

### Post by dFlyer on 2011-07-14
What other webcam software are you using with linux?

---

### Post by Snowboi on 2011-07-14
Just a quick answer here

First of all you can check the skype settings themselves.

Open up skype then sign in. From the bottom left there should be the skype logo click on it then go to options. On the it should say video devices there you can
1. Test your webcam to see if its working
2. Change which webcam skype uses
3. Enable skype video.
4. Enable automatic skype video when i enter a chat :)

If none of those work try to download and install cheese

Synaptic Package Manager > type in cheese

Or from the terminal

```
sudo apt-get install cheese
```

type in your password and press y to install.
it should then be available under applications > sound and video
If cheese is working then skype cannot detect your camera.

---

### Post by Brasileiro on 2011-07-14
Here I share the solution I've found in double language Português/English with the problem I also had with a Skype cam  in Ubuntu, I hope it helps. I think I have to share what I learn in these forums.

Right after the Portuguese version it is the English version. I hope it helps.   



 
Após dispender um bom tempo procurando e finalmente conseguindo colocar funcionando a câmera do Skype no Ubuntu 11, divido aqui uma boa solução para esta questão, resumindo o que pesquisei em várias fontes. Este texto tem três parte fundamentais onde cada um pode consultar a que melhor precisar:

1-A SOLUÇÃO BÁSICA
2-VERIFICAÇÃO DO SUPORTE
3-MONTAGEM DO MENU PARA O SKYPE COM WEBCAM




1-A SOLUÇÃO BÁSICA

A solução basicamente foi usar no terminal o comando 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

De acordo com:

[http://forum.skype.com/index.php?showtopic=505131](http://forum.skype.com/index.php?showtopic=505131)


Este comando automaticamente abre o Skype com a câmera já funcionando, o que pode ser verificado no Skype em

opções->vídeo->testar



2-VERIFICAÇÃO DO SUPORTE


Caso não funcione, a câmera pode ser identificada em linha de comando através de 

lsusb

E o driver por 

lsmod | grep videodev

E seu suporte e driver verificado em

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)


3-MONTAGEM DO MENU PARA O SKYPE COM WEBCAM

Finalmente, para aqueles que quiserem prescindir do terminal e utilizar o bom e velho menu para lançar o Skype, segue-se o procedimento que utilizei para tanto:

a)Salvar o comando

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

em um arquivo, por exemplo, skypecam

Sugiro salvar em um diretório já definido pela variável $PATH, no terminal ver:

echo $PATH

No meu caso usei:
/usr/local/sbin

b)Tornar este arquivo executável, (verificar as permissões com ls -l)
para tanto em /usr/local/sbin dar:

sudo chmod o=rx skypecam

O comando skypecam agora deve funcionar no terminal a partir de qualquer diretório.

c)Adicionar o item no menu, para tanto usar o botão direito do mouse em cima de 'Aplicativos' no painel principal, e selecionar 'Editar menus'. Clicar na linha com 'Skype' e em 'Novo item' (o novo item ficará logo após o Skype, embora sua posição no menu possa ser alterada ou arrastando o item nesta caixa de diálogos, ou as opções de mover para cima ou para baixo).

  Na janela de novo item colocar o nome, pode ser SkypeCam ou outro qualquer, o comando skypecam, e um comentário opcional. O ícone deve automaticamente ser o do skype, devido ao nome skypecam, senão pode-se escolher qualquer outro ícone para o comando skypecam. Agora a opção SkypeCam deverá estar disponível no menu

Aplicativos->Internet->SkypeCam


    O único problema deste procedimento é que o SkypeCam não fica disponível para todos os usuários automaticamente, é preciso se acrescentar manualmente o novo item de menu para cada novo usuário. Não sendo preciso, porém se fazer o arquivo skypecam, edição chmod etc.

   Existem alguns procedimentos para tornar esta tarefa automática, porém o trabalho de se encontrar os devidos arquivos para tanto não compensa para poucos usuários.

[http://tuxtweaks.com/2009/07/how-to-add-item-gnome-menu/](http://tuxtweaks.com/2009/07/how-to-add-item-gnome-menu/)
[http://www.breaknenter.org/2010/10/share-menus-between-users-in-ubuntu/](http://www.breaknenter.org/2010/10/share-menus-between-users-in-ubuntu/)

  Talvez em uma versão futura do ubuntu esta questão seja resolvida.


Fica portanto a sugestão de solução para o uso de webcams no ubuntu.



 

 

 After spending some (actually a lot of) time I finally make my Skype camera work in Ubuntu 11. I share here a good solution for this issue. Here I summarize what I've found in several resources. This text has three fundamental parts where you can consult the one you need:
 

 1-BASIC SOLUTION
 2-CHECK SUPPORT
 3-SET UP UBUNTU MENU FOR SKYPE WITH WEBCAM
 

 1-BASIC SOLUTION
 

 The basic solution was to use command line in the console
 

 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 

 According to:

[http://forum.skype.com/index.php?showtopic=505131](http://forum.skype.com/index.php?showtopic=505131)


 This command automatically opens Skype with the camera working, what you can check in
 

 options->video->test
 

 

 2-CHECK SUPPORT
 

 If it does not work, the camera can be checked in the comand line by
 

 lsusb
 

 And the drive by
 

 lsmod | grep videodev
 

 The camera support and driver can be checked in
 

 [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
 

 

 

 3-SET UP UBUNTU MENU FOR SKYPE WITH WEBCAM
 

 Finally, for those that don't want to use the command line and simply use the menu to launch Skype, here I show the procedure that I used:
 

 a)Save the command

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a file, for instance, skypecam


 I suggest to save this file in a folder already defined by the variable $PATH, in the console see:


 echo $PATH

In my case I used:
 
/usr/local/sbin
 

 

 b)Make this file executable, (check permissions with ls -l), to do so in /usr/local/sbin give the command:
 

 sudo chmod o=rx skypecam
 

 The command skypecam now should work in any console from any directory.
 

 c)Add the item in the menu.  
 

 Note: The commands here are directly translation from a Portuguese version of the Ubuntu, so they may be different from the English version.
 

 To do it use the right mouse button in the 'Application' in the main panel, and select 'Edit menus'. Click in the line with 'Skype' and in 'New item' (the new item should stay right after the Skype, although its position in the menu can be changed by dragging the item in the dialog box, or the option to move up and down).
 

 In the window for the new item put the name, can be SkypeCam or any other, the comand skypecam, and an optional comment. The icon should automatically be the one used for skype, probably because of the skypecam name, otherwise any icon can be chosen for the skypecam command. Now the SkypeCan option should appear in the menu.  
 

 Applications->Internet->SkypeCam
 

 

 The only problem with this procedure is the SkypeCam doesn't become available for all users automatically. It is needed to add manually the menu item for each new user of a computer. It is not needed, though, to do the skypecam, chmod edition, etc.
 

 

 There has some procedures to automate this task, whoever the work to find the files is worthless if the computer is used for few users.
 

 [http://tuxtweaks.com/2009/07/how-to-add-item-gnome-menu/](http://tuxtweaks.com/2009/07/how-to-add-item-gnome-menu/)
[http://www.breaknenter.org/2010/10/share-menus-between-users-in-ubuntu/](http://www.breaknenter.org/2010/10/share-menus-between-users-in-ubuntu/)


 

 That is a questions in ubuntu yet to be solved.
 

 

 

 So that is my suggestion to use webcams in ubuntu.

---

