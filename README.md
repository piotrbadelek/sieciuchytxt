# Specyfikacja Sieciuchy.txt

* [Podstawy](#Podstawy)
* [Pluginy](#Pluginy)
* [Integracje](#Integracje)
* [FAQ](#FAQ)


Sieciuchy.txt to najnowszy standard który pozwala na definiowanie informacji dla sieciuchów, jak również dla sieciaków:

Przykładowe pliki Sieciuchy.txt:

```sieciuchy
Allow: Sieciuchy
Disallow: Sieciaki
```

```sieciuchy
Allow: Sieciuchy
Allow: Czyste zło
Allow: Bełkot
Allow: Kradziej
Allow: Kłamacz
Allow: Śmieciuch
Disallow: Sieciaki
Disallow: NetRobi
Disallow: Ajpi
Disallow: Kompel
Disallow: Netka
Disallow: Spociak
```

```sieciuchy
Allow: Sieciuchy
Disallow: Sieciaki
Allow: NetRobi | /rickroll
```

## Podstawy

Aby zacząć regulować sieciuchy i sieciaki na twoim serwerze WWW, stwórz plik sieciuchy.txt w katalogu głównym swego serwera - tak aby można było się do niego dostać wpisując `http://twojastro.na/sieciuchy.txt`.

### Struktura Pliku

Plik zgodny ze standardem sieciuchy.txt będzie miał taką strukturę:

```
Akcja: Osoba | Path (Opcjonalne)
```

W praktyce, wygląda to tak:

```
Allow: Czyste zło
Disallow: Bełkot | /dokumenty-czystego-zla.pdf
```

Kod przedstawiony powyżej sprawia że Czyste Zło może korzystać ze wszystkich stron na serwerze, a Bełkot nie może korzystać z `http://twojastro.na/dokumenty-czystego-zla.pdf` - wszystkie inne strony są dla niego jednak dostępne.

### Akcje

Dostępne akcje to `Allow` i `Disallow`.
- Allow - Pozwala na dostęp.
- Disallow - Nie pozwala na dostęp.

### Osoby

Dostępne osoby do blokowania/odblokowania to:
- Sieciuchy (Wszystkie sieciuchy)
- Czyste zło
- Bełkot
- Kradziej
- Kłamacz
- Śmieciuch
- Sieciaki (Wszystkie Sieciaki)
- NetRobi
- Ajpi
- Kompel
- Netka
- Spociak

### Path

Specyfuje on dokładnie jakie materiały są dostępne/niedostępne.

## Pluginy

Pluginy do Sieciuchy.txt pozwalają na niestandardowe informacje dla sieciaków/sieciuchów.

Przykładowy plik sieciuchy.txt z pluginami:

```
@extends("/superpliki/mojPlugin.html");
Allow: Sieciuchy
Disallow: Sieciaki @mojPlugin("redirect", "https://www.youtube.com/watch?v=dQw4w9WgXcQ")
```

Plik .html z pluginem to tak naprawdę dokument ze specyfikacją pluginu.
Parser pliku sieciuchy.txt powinnen zrequestować plik z podanym pluginem i jeśli nie potrafi go obsłużyć powinnen poprostu go zignorować. Jeśli jednak plugin może być obsłużony, dodatkowe instrukcje związane z pluginem powinny być uruchomione.

Przykładowy plik z specyfikacją pluginu:

```html
<div itemscope itemtype="https://github.com/ProgramistaZpolski/sieciuchytxt/blob/master/README.md#pluginy">
	<h1 data-sieciuchy-plugin="pluginName">Sieciuchy.txt redirect plugin</h1>
	Ut a culpa praesentium non. Temporibus ea tempora eum eum praesentium similique nam veniam. Voluptatibus voluptatibus ipsam consequatur nihil dolorum quidem soluta. Consequatur dolorum aliquid doloribus voluptatem sunt vel ea dolor.

	Voluptatem saepe in tenetur distinctio temporibus quo. Recusandae quasi est accusantium saepe nihil delectus sint error. Est impedit incidunt quod. Consequatur nemo hic rerum illum dolorem odit doloribus aliquid. Voluptas ea officiis sed est.
</div>
```

Podany Itemscope, Itemtype, oraz data-sieciuchy-plugin są wymagane w specyfikacji pluginu Sieciuchy.

## Integracje

### HTML
Jeśli chcesz oznajmić w kodzie swej witryny że obsługujesz sieciuchy txt, dodaj do swojego tagu \<html\> atrybut data-sieciuchy - Przykład:
```html
<html lang="pl" dir="ltr" data-sieciuchy="/sieciuchy.txt">
```

## FAQ

Q: Dlaczego w takim pliku:
```
Allow: Sieciuchy
Allow: Czyste zło
Allow: Bełkot
Allow: Kradziej
Allow: Kłamacz
Allow: Śmieciuch
Disallow: Sieciaki
Disallow: NetRobi
Disallow: Ajpi
Disallow: Kompel
Disallow: Netka
Disallow: Spociak
```
Są kilka razy sprecyzowane sieciuchy i sieciaki?

A: Jest to zabezpieczenie - jeśli np. Kradziej przestanie być sieciuchem, dalej chcemy blokować mu stronę.
