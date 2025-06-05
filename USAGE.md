# Richtlinien zur Nutzung von Manubot

Dieses Repository verwendet [Manubot](https://manubot.org), um automatisch ein Manuskript aus der Quelle im Verzeichnis [`content`](content) zu erstellen.

Im [Manubot-Katalog](https://manubot.org/catalog/) finden Sie Beispiele dafür, was beim Schreiben mit Manubot möglich ist.

Versuchen Sie, das [Demo-Manuskript](https://github.com/manubot/try-manubot) zu bearbeiten, um die Manubot-Formatierung und Zitate schnell zu testen.

## Manubot Markdown

Manuskripttext sollte in Markdown-Dateien geschrieben werden, die sich im Verzeichnis [`content`](content) befinden.

Markdown-Dateien werden durch ihre Erweiterung `.md` identifiziert und nach ihrem zweistelligen Präfix sortiert (z.B. `01. `, `02. `, ... `99. `).

Für grundlegende Formatierungen finden Sie auf der Seite [CommonMark Help](https://commonmark.org/help/) eine Einführung in die Formatierungsoptionen, die von Standard-Markdown bereitgestellt werden.

Darüber hinaus unterstützt Manubot eine erweiterte Version von Markdown, die auf wissenschaftliches Schreiben zugeschnitten ist und [Pandoc's Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown) und die unten diskutierten Erweiterungen enthält.

Die Datei `content/02.delete-me.md` im Rootstock-Repository zeigt viele der von Manubot unterstützten Elemente und Formatierungsoptionen.

Siehe das [raw markdown](https://gitlab.com/manubot/rootstock/blob/main/content/02.delete-me.md#L) in dieser Datei und vergleichen Sie es mit dem [gerenderten Manuskript](https://manubot.github.io/rootstock/).

Innerhalb eines Absatzes in Markdown werden einzelne Zeilenumbrüche als Leerzeichen interpretiert (gleich wie ein Leerzeichen).

Die Quelle eines Absatzes muss keine Zeilenumbrüche enthalten.

"Ein Absatz pro Zeile" macht den Git-Diff jedoch weniger präzise, was zu weniger detaillierten Überprüfungskommentaren führt und Konflikte wahrscheinlicher macht.

Daher empfehlen wir die Verwendung von [semantic linefeeds](https://rhodesmill.org/brandon/2012/one-sentence-per-line/ "Semantic Linefeeds. Brandon Rhodes. 2012") - Zeilenumbrüche zwischen den Sätzen.

Wir haben festgestellt, dass "ein Satz pro Zeile" "Wortumrasung" oder "ein Absatz pro Zeile" vorzuziehen ist.

### Tische

Manubot unterstützt [Markdown-Tabellen](https://help.github.com/articles/organizing-information-with-tables/ "GitHub Help: Organisieren von Informationen mit Tabellen").

```md

| Spalte 1 | Spalte 2 | Spalte 3 |

|----------|----------------|--------|

| Wert_a | 1 | 47 |

| Wert_b | 2 | 56 |

Tabelle: Beschriftung für diese Beispieltabelle. {#tbl:example-id}

```

Unterstützung für Tabellennummerierung und Zitieren wird durch [`pandoc-tablenos`](https://github.com/tomduck/pandoc-tablenos) bereitgestellt.

Oben setzt `{#tbl:example-id}` die Tabellen-ID, die einen HTML-Anker erstellt und es ermöglicht, die Tabelle als `@tbl:example-id` zu zitieren.

Für die einfache Erstellung von Markdown-Tabellen sehen Sie sich die Webapp [Tables Generator](https://www.tablesgenerator.com/markdown_tables) an.

### Zahlen

Die Zahlen können mit dem folgenden Markdown aufgenommen werden:

```md

![ Bildunterschrift für die Beispielfigur.](url_or_path_to_figure){#fig:example-id}

```

Die Leerzeile vor der Figur ist erforderlich.

Unterstützung für die Zahlennummerierung und das Zitieren wird von [`pandoc-fignos`](https://github.com/tomduck/pandoc-fignos) bereitgestellt.

Diese Figur kann im Text mit `@fig:example-id` zitiert werden.

Im Kontext kann ein Zahlenzitat wie folgt aussehen: `Figur {@fig:example-id}B zeigt ...`.

Für Bilder, die von den Manuskriptautoren erstellt wurden und an anderer Stelle auf GitHub gehostet werden, empfehlen wir die Verwendung einer [versionierten](https://help.github.com/articles/getting-permanent-links-to-files/) GitHub-URL, um Abbildungen einzubetten und so die genaue Bildherkunft zu erhalten.

Beim Einbetten von SVG-Bildern, die auf GitHub gehostet werden, ist es notwendig, `? Sanitize=true` zur URL `raw.githubusercontent.com`.

Zum Beispiel:

```

Https://raw.githubusercontent.com/greenelab/scihub/572d6947cb958e797d1a07fdb273157ad9154273/figure/citescore.svg? Desinfizieren=wahr

```

Abbildungen, die im Verzeichnis [`content/images`](content/images) platziert sind, können mit ihrem relativen Pfad eingebettet werden.

Zum Beispiel betten wir ein [ORCID](https://orcid.org/)-Symbol inline ein, indem wir:

```md

![ ORCID-Symbol](images/orcid.svg){height="13px"}

```

Der Text in Klammern nach der Bilddeklaration wird durch die Erweiterung [`link_attributes`](https://pandoc.org/MANUAL.html#extension-link_attributes) von Pandoc interpretiert.
