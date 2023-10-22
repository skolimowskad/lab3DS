# lab3 Dominika Skolimowska

Plik YAML definijue poda sidecar-pod w przestrzeni nazw lab3.
Pod zawiera dwa kontenery: busybox-container i nginx-container.
Pierwszy z nich uzywa obrazu busybox. Co 5 sekund zapisuje biezaca date do wskazanego pliku.
Drugi kontener uzywa obrazu nginx. Ma on dostep do wspomnianego wczesniej pliku poprzez wspoldzielony wolumin typu hostPath.

Do utworzenia tego poda nalezy wykorzystac kubectl i polecenie
_kubectl apply -f lab3DS.yaml_
Aby potwierdzic poprawnosc dzialania poda nalezy wykonac nastepujace polecenia
_kubectl port-forward -n lab3 sidecar-pod 8080:80_
oraz _curl http://localhost:8080/date.log_

Powyższe polecenia ustanawiają połączenie do serwera nginx uruchomionego w kontenerze nginx-container i pobierają dane z pliku /var/log/date.log.
