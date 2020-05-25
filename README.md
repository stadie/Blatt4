Sie finden diese Aufgabe auf github:
<https://classroom.github.com/g/oNIsJyv7>.

Mit dem Programm **zufall.cc** soll der Wert der Kreiszahl $\pi$
berechnet werden. Daf\"ur werden zuf\"allig \"uber den Bereich
$-1 < x < 1$ und $-1 < y < 1$ $N$ Punkte $(x,y)$ (gleich-)verteilt und
gez\"ahlt, wie viele dieser Punkte innerhalb eines Kreises um den
Ursprung mit Radius $r=1$ liegen. Das Verh\"altnis der Anzahl der Punkte
im Kreis $N_{in}$ und der Gesamtzahl $N$ entspricht dem Verh\"altnis der
Fl\"achen des entsprechenden Kreises und Quadrats
$\frac{N_{in}}{N}= \frac{\pi 1^2}{2 \cdot 2}$. Durch Umformen ergibt
sich dann $\pi$.

Schreiben Sie das Hauptprogramm, das \"uber eine for-Schleife die $N$
Punkte zuf\"allig erzeugt und z\"ahlt, wie viele im Kreis liegen.
Implementieren Sie zudem am Ende des Hauptprogramms die Berechnung des
Sch\"atzwertes f\"ur $\pi$. Damit das Programm funktioniert, muss noch
eine Funktion `double zufall()` implementiert werden, die Zufallszahlen
zwischen 0 und 1 erzeugen soll. Verwenden Sie hierzu den linear
kongruenten Generator aus der Vorlesung:\
$I_j = (a \cdot I_{j-1}+c) \mod m$ und $u_j = \frac{I_j}{m}$.\
Verwenden Sie zum Testen:\

   a     5      205
  --- ---- --------
   c     3    29573
   m    16   139968

\
Damit Ihre Funktion `double zufall()` nicht immer den gleichen Wert
zur\"uckliefert, muss sie sich den Wert von $I_j$ des letzten Aufrufs
merken. Dies erreichen Sie, indem Sie die Variable in der $I_j$
gespeichert wird, als statisch deklarieren (Schl\"usselwort: `static`).

Vergleichen Sie die Genauigkeit der Bestimmung von $\pi$ f\"ur
verschiedene Anzahlen an verwendeten Zufallszahlen
$N = 100, 10^4, 10^5,  10^6$ und verschiedene Konstanten $a$, $c$, $m$.
Welche Genauigkeit erwarten Sie (mit einer Binomialverteilung mit
$p=\pi/4$)?\
Anmerkung: Der Erwartungswert der Binomialverteilung ist $E[N_{in}]=pN$
und die Varianz $V[N_{in}]=p(1-p)N$. Das gesuchte $\pi$ errechnet sich
aus $\pi= 4\frac{N_{in}}{N}$ und \"uber Fehlerfortpflanzung erh\"alt man
$\sigma_{\pi} = \frac{d\pi}{dN_{in}} \sqrt{V[N_{in}]} = 4 \frac{\sqrt{V[N_{in}]}}{N}$.\

  Einstellung                              $N$  $E[N_{in}]$   $V[N_{in}]$   $N_{in}$   $\pi$   $\sigma_{\pi}$
  -------------------------------- ----------- ------------- ------------- ---------- ------- ----------------
  $a=5$, $c=3$, $m=16$                     100     78,5          16,9                         
  $a=205$, $c=29573$, $m=139968$           100     78,5          16,9                         
  $a=5$, $c=3$, $m=16$                  10 000                                                
  $a=205$, $c=29573$, $m=139968$        10 000                                                
  $a=5$, $c=3$, $m=16$                 100 000                                                
  $a=205$, $c=29573$, $m=139968$       100 000                                                
  $a=5$, $c=3$, $m=16$               1 000 000                                                
  $a=205$, $c=29573$, $m=139968$     1 000 000                                                
