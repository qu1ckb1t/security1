# Домашнее задание к занятию "`Уязвимости и атаки на информационные системы`" - `Аблогин Павел`

---

### Задание 1

1. `Разрешенные сетевые службы на хосте с metasploitable:`
```
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain      ISC BIND 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login       OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
```

2. `Обнаруженные уязвимости:`
```
  1. vsftpd 2.3.4 - Backdoor Command Execution 
     https://www.exploit-db.com/exploits/49757

  2. MySQL 5.0.x - IF Query Handling Remote Denial of Service   
     https://www.exploit-db.com/exploits/30020

  3. PostgreSQL 8.3.6 - Conversion Encoding Remote Denial of Service 
     https://www.exploit-db.com/exploits/32849

```

---

### Задание 2

1. `Провел сканирование VM Metasploitable в режимах SYN, FIN, Xmas, UDP.`
2. `Записал сеансы сканирования в файл scan.pcap (приложил)`
3. `Отличие режимов сканирования и ответ сервера: `
```
SYN - скан TCP-портов. Отправка пакета с флагом открытия (установки) соединения, после получения от сканируемого хоста пакета подтверждения SYN/ACK (значит порт открыт) прерывание соединения; 
FIN - скан TCP-портов. Отправка пакета на закрытие соединения (FIN), если в ответ приходит RST , то порт считается закрытым, иначе открыт или фильтруется файерволом;
Xmas - скан TCP-портов. Отправка пакета с установленными флагами FIN, PSH, URG. Ответ аналогичный FIN. 
UDP - сканирование UDP портов. Отправка UDP пакета без данных, или с данными , специфичными для конкретного сервиса. Возврат ICMP port unreachable error (type 3, code 3) означает, что порт закрыт; другие ICMP unreachable ошибки (type 3, codes 0, 1, 2, 9, 10, or 13) указывают, что порт фильтруется.  
```

`[Файл дампа трафика сканирования](files/scan.pcap)`

---
