# sql-bootcamp-week7
-- ===============================================================================
-- Fase 2 — Análisis: identificar las violaciones
-- ===============================================================================
-- Violación de 1FN (Valores multivalor / No atómicos):
-- Las columnas productos, categorias, precios, cantidades y descuentos almacenan arreglos/listas separados por comas dentro de una sola celda.

-- Violación de 2FN (Dependencias Parciales):
-- Al aplanar los detalles de venta, los atributos del vendedor (vendedor_email, etc.) y del cliente (cliente_email, etc.) dependen únicamente del ID de la Venta o del Cliente/Vendedor, no de la combinación Venta-Producto.

-- Violación de 3FN (Dependencias Transitivas):
-- El jefe del departamento (vendedor_depto_jefe) depende de vendedor_departamento, no directamente del vendedor.
-- La categoría pertenece al producto, no a la transacción.
-- Los datos de ubicación (cliente_estado, cliente_pais) dependen de la ciudad o del cliente.

**Anomalías reales que sufre esta base** 
-- Anomalía de actualización: si Ana cambia su email, hay que actualizar N filas (todas las ventas que ella hizo). Si olvidas una, queda inconsistente.
-- Anomalía de inserción: ¿cómo registras un nuevo departamento que aún no tiene vendedores? No puedes — la única forma de crear filas es a través de una venta.
-- Anomalía de eliminación: si borras la última venta de "María González", se va María completa — la base ya no sabe que existe esa cliente.
-- Redundancia masiva: "Carlos López" como jefe de Ventas se repite en cada fila de Ana y Pedro. "México" se repite en cada cliente mexicano.
