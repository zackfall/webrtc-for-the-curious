---
title: FAQ
type: docs
weight: 12
---

# FAQ

{{<details "¿Por qué WebRTC usa UDP?">}}
La NAT Transversal requiere UDP. Sin la NAT Transversal, establecer una conexión P2P
no sería posible. UDP no provee una "entrega garantizada" como TCP, así que WebRTC lo hace a nivel de
usuario.

Mira [Conexión]({{< ref "03-connecting" >}}) para más información.
{{</details>}}

{{<details "¿Qué tantos DataChannel puedo tener?">}}
65534 canales como identificador de flujo tiene 16 bits. Puedes cerrar y abrir uno nuevo cuando quieras
{{</details>}}

{{<details "¿WebRTC tiene limites en el ancho de banda?">}}
Tanto los DataChannels y RTP usan un control de congestión. Esto significa que WebRTC mide activamente
tu ancho de banda e intenta usar la cantidad óptima. Es un balance entre mandar cuanto más se pueda,
sin sobrecargar la conexión.
{{</details>}}

{{<details "¿Puedo mandar datos binarios?">}}
Si, puedes mandar datos en texto o binario vía DataChannels.
{{</details>}}

{{<details "¿Qué latencia puedo esperar con WebRTC?">}}
Para medios sin ajustar, puedes esperar menos de 500 milisegundos. Si estás dispuesto a
ajustar o sacrificar la calidad por latencia, los desarrolladores han conseguido menos de
100 milisegundos de latencia.

Los DataChannels soportan la opción de "Confiabilidad parcial" la cual puede reducir la latencia
causada por los datos retransmitidos por una perdida de conexión. Si se configura correctamente,
se ha demostrado que supera las conexiones TCP y TLS.
{{</details>}}

{{<details "¿Por qué querría una entrega desordenada de DataChannels?">}}
Cuando la nueva información deja obsoleta a la anterior, como la información de posición
de un objeto, o cada mensaje es independiente de los demás y necesita evitar
el retraso por el bloqueo de encabezado de línea.
{{</details>}}

{{<details "¿Puedo mandar audio o vídeo a través de un DataChannel?">}}
Si, puedes mandar cualquier dato a través de un DataChannel. En el casos del navegador,
será tu responsabilidad descifrar los datos y pasarlos a un reproductor multimedia para renderizar,
mientras que todo eso se hace automáticamente si se usa canales multimedia.
{{</details>}}
