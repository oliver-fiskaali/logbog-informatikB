# Logbog
**Logbog af Informatik-projekter:**

**3D-print**

Terning:

Formel: Længde * Bredde * Højde

Mine mål: 2 * 2 * 2 = 8 cm3

Jeg har lavet min terning ved at starte med at skitsere en firkant og derefter brugt “extrude”-funktionen, for at trække i den og gøre den tredimensionel.

Cylinder:

Formel: Grundflade (π * r2) * Højde

Mine mål: 4,9 (π * 1,252) * 2 = 9,8 cm3

Jeg har lavet min cylinder ved at starte med at skitsere en cirkel og derefter brugt “extrude”-funktionen, for at trække i den og gøre den tredimensionel.

Kugle: 

Formel for rumfang: 4/3 * π * r3

Mine mål: 4/3 * π * 1,253 = 8,177 cm3

For at lave min kugle har jeg brugt “Sphere”-funktionen. Med “Sphere”-funktionen er der så blevet udarbejdet en kugle ud fra mit valg af radius på 1,25 cm.

**Dronecontroller**

**Kort beskrivelse af projekt:**

Vi har efter vores brainstorm valgt at lave en form for "Dance Dance Revolution"-agtig controller.

**Brugerundersøgelse:**

Ved hjælp af vores brugerundersøgelse har vi tænkt os at teste controllerens præcision, sikkerhed og respons, samt brugerens oplevelse. Vores brugerundersøgelse foregår på en bane, som brugeren skal gennemføre. Derefter vil vi stille nedenstående spørgsmål til brugeren, for at få en indsigt i hvordan nye brugere har det med at bruge controlleren. Derudover observere vi også selv dronens opførsel og eventuelle ting som kan forbedres. Vi har tænkt os at transskribere brugerens svar. 

Spørgsmål til brugeren:
Er controlleren nem at bruge? Er der noget indlysende, som du synes kan optimeres?

Hvad synes du om designet? 

Er der nogle design-relaterede ting på controlleren som du ville ændre? Hvis ja, hvad? 

Er knapperne placeret godt i forhold til hinanden eller kunne man gøre det lettere at styre dronen ved at rykke nogle af knapperne?

Er controller-respons ved tryk af knapper god? Er responstiden god?

Er der nogle manglende funktioner, som kunne gøre det lettere at flyve dronen? (OBS, kun i forhold til basisk at flyve dronen, ikke nogle ekstra funktioner, kamera-relateret eller lignende.)

Opstilling af drone-bane/mål for dronen:
For optimalt at teste alle dronens aspekter opsætter vi en form for bane, som brugeren skal gennemføre. Mens brugeren gennemgår banen, skal vi observere dronens bevægelser. Banen er lavet sådan at den både tester controllerens præcision, sikkerhed og respons.
Vores bane foregår uden for vores klasselokale, D2304. Man starter og flyver rundt om de to stolper hvorefter man skal ramme et stykke pap, som er vores slutpunkt. Dette er med til at teste både controllerens og brugerens præcision.


**Brainstorm:**

Fodstyret controller:
Meningen ville være at skabe en form for sko, som man skulle tage på sin fod. Den sko skulle så på en eller anden måde være koblet til dronen, så dronen ville rykke sig, som man rykkede sin fod.

Håndstyret controller:
Samme idé som fodstyret, men med en handske.

Fjernbetjening:
En form for klassisk controller med knapper og joystick til styring.

Eyetracker:
Dronen ville være styret af øjnene. Den ville rykke sig efter hvordan man flyttede sine øjne.

Autopilot:
Tanken var at programmere en autopilot, som kunne flyve dronen sikkert.

Hjernestyret:
På en måde få dronen til at flytte sig efter hjernens tanker.

Led-styring:
Dronen skulle styres efter bøjning af led på arme og ben. 

Face-recognition:
Tanken var at få dronen til at genkende ansigter når den så dem og så derefter flyve direkte mod deres ansigt.

**Kort beskrivelse af gestaltlove:**

1) Nærhed (proximity). Figurer der er placeret tæt på hinanden ses som en gruppe.
2) Lighed (similarity invarians). Ens figurer opfattes som en gruppe.
3) Lukkethed (closure). Delelementer af et billede stykkes sammen til at skabe helheden.
4) Kontinuitet og symmetri. Optræder to figurer symmetriske omkring en linje, ses de som en gruppe.
5) Prægnans (Prägnanz) – figur/baggrund. Hjernen leder den efter mønstre, kontinuitet, ensartethed.
6) Erfaring (Past experience, “Common Fate”). Dækker bl.a. over brugen af ikoner
7) Forbundethed – Forbindes figurer med en streg, opfattes de umiddelbart som sammenhørende (forbundenhed er et design tips – ikke en gestaltlov).

**Kode til 'Seriel-split finder'**

import serial import tellopy import sysdef Hej(): if (rxLine == “Ned”): print(“ned”) if (rxLine == “Op”): print(“op”)if (rxLine == “Ventre”): print(“venstre”) if (rxLine == “Hojre”): print(“højre”)if (rxLine == “Hdrej”): print(“svingh”) if (rxLine == “Vdrej”): print(“svingv”)if (rxLine == “Frem”): print(“frem”) if (rxLine == “Tilbage”): print(“tilbage”)serialPortName = “COM5” baudRate = 9600 try: s = serial.Serial(serialPortName,baudRate,timeout=1)except: print(“Failed to open”, serialPortName, “as a serial port.. are you doingthis right?”) sys.exit(1)print(“Shit, it worked.. waiting for serial data. . . ”)try: while(s.is_open):if(s.in_waiting>0):rxLine=s.readline().decode("ascii").strip()Hej()except: Hej()1

**Test af TELLO-Drone ved hjælp af indbyggede commands**

import tellopy import time import keyboarddrone = tellopy.Tello()drone.connect()drone.takeoff() while True: try: while (keyboard.is_pressed(“f”)): drone.down(40)(keyboard.on_release(“f”)):    drone.up(40)  if  (keyboard.is_pressed(“r”)):drone.up(40)  if  (keyboard.on_release(“r”)):    drone.down(40)  if  (key-board.is_pressed(“a”)):drone.left(40)   if   (keyboard.on_release(“a”)):drone.right(40)  if  (keyboard.is_pressed(“d”)):   drone.right(40)  if  (key-board.on_release(“d”)):drone.left(40)   if   (keyboard.is_pressed(“q”)):drone.counterclockwise(100) if (keyboard.on_release(“q”)): drone.clockwise(100)if (keyboard.is_pressed(“e”)): drone.clockwise(100) if (keyboard.on_release(“e”)):drone.counterclockwise(100) if (keyboard.is_pressed(“w”)): drone.forward(50) if(keyboard.on_release(“w”)): drone.backward(50) if (keyboard.is_pressed(“s”)):drone.backward(50)  if  (keyboard.on_release(“s”)):   drone.forward(50)  if(keyboard.is_pressed(“p”)): drone.land() except: drone.land()1

**Privathed, sikkerhed, passwords:**

Under dette forløb har vi blandt andet set filmen 'Snowden'.
I dette forløb har vi sat fokus på om overvågning. Det har vi gjort ved både at kigge på hvor meget vi bliver overvåget på nettet, men også individ-overvågning, som er nårder bliver sat fokus på én person. Dette kan både være pga. kriminalitet, at der bliver set på hvad man laver, men det kan også være at man kan blive udsat for overvågning efter at have trykket på et link eller downloaded noget, som man ikke skulle have gjort.
Vi har også sat stort fokus på passwords sikkerhed. Vi har bl.a. kigget på programmer som simpelthen er lavet til at nedbryde passwords vha. wordlists.
Dermed har vi også brugt hjemmesiden http://security.org til at tjekke sikkerheden af diverse passwords. Med den er vi kommet frem til at det er forholdsvis sikkert med password på 12+ karakterer da det vil tage en computer 41 år at nedbryde et sådan password.
