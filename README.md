## Objetivo
Reproducir un error típico al hacer VNet Peering: dos redes con rangos de IP que se solapan. Identificar la causa, corregir el address space y dejar el peering en estado conectado.

## Qué ha pasado (incidencia)
Al intentar emparejar dos VNets, Azure bloquea el peering porque los espacios de direcciones tienen solapamiento. Con peering, las redes deben ser únicas para poder enrutar correctamente.

## Resolución
He modificado el address space de una de las VNets para eliminar el solapamiento y, tras eso, el peering ha quedado en estado **Connected**.

## Evidencias

### 01 – Error por solapamiento (IP Overlap)
<img src="images/01-ip-overlap-error.png" width="800">

### 02 – Cambio de address space para evitar solapamiento
<img src="images/02-address-space-change.png" width="800">

### 03 – Peering en estado Connected
<img src="images/03-peering-connected.png" width="800">

## Qué diría en entrevista
“Cuando un peering falla por IP overlap, no es un problema de permisos: es de diseño de red. Lo resuelvo ajustando CIDR para que no se solapen y validando el estado del peering.”
