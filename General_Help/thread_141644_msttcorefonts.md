---
title: "msttcorefonts"
date: 2006-03-08
forum: General Help
---

### Post by Robben on 2006-03-08
if anyone know how to fix this please help me.
thanks in advance..

```
filipe@ubuntu:~$ sudo apt-get install msttcorefonts
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
msttcorefonts já é a versão mais recente.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
É necessário fazer o download de 0B de arquivos.
Depois descompactar, 0B adicionais de espaço em disco serão utilizados.
A instalar msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--21:07:03--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Tempo esgotado para conexão.
--21:07:13--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Tempo esgotado para conexão.
--21:07:23--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Tempo esgotado para conexão.
--21:07:33--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... failed: Tempo esgotado para conexão.
Desistindo.

--21:07:46--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... 195.113.161.88
Connecting to cesnet.dl.sourceforge.net|195.113.161.88|:80... failed: Tempo esgotado para conexão.
Desistindo.

--21:07:59--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Tempo esgotado para conexão.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: erro ao processar msttcorefonts (--configure):
 subprocesso post-installation script retornou erro do status de saída 1
Foram encontrados erros enquanto processava:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
filipe@ubuntu:~$
```

---

### Post by müller on 2006-03-08
connection with switch.dl.sourceforge.net faild:
Resolving switch.dl.sourceforge.net... failed: Tempo esgotado para conexão.

try again later
and check your sources list.

---

